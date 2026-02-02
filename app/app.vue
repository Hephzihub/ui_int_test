<script setup>
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/favicon.png' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'UI Interview Test'
const description = 'UI implementation interview test using Nuxt UI template.'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  // ogImage: 'https://ui.nuxt.com/assets/templates/nuxt/starter-light.png',
  // twitterImage: 'https://ui.nuxt.com/assets/templates/nuxt/starter-light.png',
  // twitterCard: 'summary_large_image'
})
</script>

<template>
  <UApp>
    <LayoutHeader />
    <UMain>
      <NuxtPage />
    </UMain>
    <LayoutFooter />
  </UApp>
</template>
