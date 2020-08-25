<template>
  <div class="flex justify-center items-center text-center">
    <div class="mt-12">
      <h1 class="font-bold text-4xl">blog-template</h1>
      <p class="mt-4">
        Hello! This is a blog template using Nuxt with the Content module!
      </p>
      <ul class="mt-8">
        <li>
          <nuxt-link to="/about">About</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/blog">Blog</nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>
