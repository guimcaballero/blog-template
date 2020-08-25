<template>
  <div class="flex justify-center items-center text-center">
    <div class="mt-12">
      <h1 class="font-bold text-4xl">About</h1>

      <div class="px-12 lg:px-64 mt-4 mb-32 text-left">
        <nuxt-content :document="page" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  async asyncData({ $content }: any) {
    const page = await $content('about').fetch()

    return {
      page,
    }
  },
})
</script>
