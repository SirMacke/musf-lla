<template>
  <div>
    <VitePwaManifest />
    <NuxtLoadingIndicator />
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<script setup>
useHead({
  link: [
    {
      rel: 'icon',
      href: '/favicon.ico',
      sizes: 'any'
    },
    {
      rel: 'icon',
      href: '/favicon.svg',
      type: 'image/svg+xml'
    },
    {
      rel: 'apple-touch-icon',
      href: '/pwa-192x192.png'
    }
  ]
});
</script>

<style lang="sass">
html
  scroll-behavior: smooth
  overflow: hidden

body
  font-family: "Lato", "sans-serif"
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  color: $color-1
  background-color: $white-2
  -webkit-tap-highlight-color: transparent
  margin: 0px
  overflow: hidden
  
h1, h2, h3, h4, h5, h6
  font-family: "CabinSketch", "sans-serif"

p
  font-size: 1.1em

a
  font-size: 1.1em
</style>