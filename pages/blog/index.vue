<template>
  <div class="flex justify-center items-center text-center">
    <div class="mt-12">
      <h1 class="font-bold text-4xl">Posts</h1>

      <div class="px-12 lg:px-64 mt-4 mb-32 text-left">
        <div
          v-for="(group, i) in Object.keys(grouped || {})"
          :key="i"
          class="mb-8"
        >
          <h2>
            <code>{{ group }}</code>
          </h2>
          <br />
          <div v-for="(elem, i) in grouped[group]" :key="i" class="mb-8">
            <nuxt-link :to="`/blog/${elem.slug}`">{{ elem.title }}</nuxt-link>
            <p v-if="elem.description" class="text-gray-600">
              {{ elem.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

type Post = {
  slug: string
  createdAt: Date
  title: string
  description: string | null
}

export default Vue.extend({
  head() {
    return {
      title: 'Blog',
    }
  },
  async asyncData({ $content }: any) {
    let posts: Array<Post> = await $content('blog')
      .only(['slug', 'createdAt', 'title', 'description'])
      .fetch()
    posts = posts
      .map((post: Post) => {
        post.createdAt = new Date(post.createdAt)
        return post
      })
      .sort((a: Post, b: Post) => +b.createdAt - +a.createdAt)

    const monthNames = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December',
    ]
    const grouped = posts.reduce(
      (groups: { [keys: string]: Array<Post> }, item) => {
        const month = item.createdAt.getMonth()
        const year = item.createdAt.getFullYear()
        const val = monthNames[month] + ' ' + year
        groups[val] = groups[val] || []
        groups[val].push(item)
        groups[val].sort((a, b) => +b.createdAt - +a.createdAt)
        return groups
      },
      {}
    )

    return { grouped }
  },
})
</script>
