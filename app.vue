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

</script>

<style lang="sass">
html
  scroll-behavior: smooth
  -webkit-user-select: none
  -khtml-user-select: none
  -moz-user-select: none
  -ms-user-select: none
  user-select: none
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