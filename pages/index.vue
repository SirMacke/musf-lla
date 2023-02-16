<template>
  <div>
    <h1 id="h1">Musfälla</h1>
    <main>
      <div class="item">
        <img src="/images/mouse-trap-100.png">
        <div class="text">
          <h2>Aktiva Fällor</h2>
          <p>3</p>
        </div>
      </div>
      <div class="item">
        <img src="/images/mouse-trap-mouse-100.png">
        <div class="text">
          <h2>Fångade Möss</h2>
          <p>1</p>
        </div>
      </div>
    </main>
    <footer>
      <NuxtLink to="/add">New Mouse Trap</NuxtLink>
    </footer>
  </div>
</template>

<script setup>
//const cookie = useCookie('auth');
//console.log('cookie', cookie)
//if (cookie == null || cookie == undefined || cookie.value == undefined || cookie.value == '') await navigateTo('/login');
</script>

<style lang="sass">
#h1
  position: absolute
  top: 20%
  margin: 0px auto
  left: 50%
  transform: translateX(-50%)
  font-size: 3em

main
  display: grid
  grid-template-rows: 1fr 1fr
  position: absolute
  left: 50%
  top: 50%
  transform: translate(-50%, -50%)

  .item
    display: flex
    margin: 20px

    img
      height: 100px
      width: 100px
      object-fit: cover

    .text
      display: flex
      flex-direction: column

      h2
        margin: 20px 0px 0px 25px

      p
        margin: 10px 0px 0px 25px
        font-size: 1.5em

@keyframes footerSlideFromRight
  0%
    opacity: 0
    left: 50px
  100%
    opacity: 1
    left: 0px

footer
  position: absolute
  bottom: 0px
  width: 100%
  height: 75px
  animation: footerSlideFromRight ease-in-out 1s 1 2s forwards
  opacity: 0
  display: flex

  a
    position: absolute
    top: 50%
    transform: translateY(-50%)
    right: 30px
    text-decoration: none
    color: $color-1

  a:hover
    text-decoration: underline
</style>