<template>
  <div class="flex justify-center items-center text-center">
    <div class="mt-12">
      <h1 class="font-bold text-4xl" v-html="page.title"></h1>

      <div class="px-12 lg:px-64 mt-4 mb-32 text-left">
        <div
          class="font-light"
          v-html="
            `${new Date(page.createdAt).toLocaleDateString()} - ${
              page.readingTime
            }`
          "
        ></div>
        <br />
        <nuxt-content :document="page" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import * as fs from 'fs'
export default Vue.extend({
  head() {
    return {
      title: (this as any).page.title,
    }
  },
  async asyncData({ $content, params }: any) {
    const page = await $content('blog', params.slug).fetch()
    return {
      page,
    }
  },
})
</script>
