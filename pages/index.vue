<template>
  <div>
    <addTrap v-if="addTrapActive" />
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
      <div id="addTrapButton" @click="changeAddTrapState">+</div>
    </footer>
  </div>
</template>

<script setup>
//const cookie = useCookie('auth');
//console.log('cookie', cookie)
//if (cookie == null || cookie == undefined || cookie.value == undefined || cookie.value == '') await navigateTo('/login');

let addTrapActive = useState('addTrapActive', () => false);

function changeAddTrapState() {
  addTrapActive.value = !addTrapActive.value;
  console.log(addTrapActive);
}
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

@keyframes footerSlideFromLeft
  0%
    opacity: 0
    left: -50px
  100%
    opacity: 1
    left: 0px

footer
  position: absolute
  bottom: 0px
  width: 100%
  height: auto
  animation: footerSlideFromLeft ease-in-out 1s 1 1s forwards
  opacity: 0
  display: flex

  #addTrapButton
    position: relative
    left: 25px
    bottom: 25px
    padding: 10px 22.5px
    text-decoration: none
    color: $white-2
    font-size: 2.5em
    background: $color-3
    border-radius: 5px

    &:hover
      background: $color-2
      cursor: pointer
      box-shadow: 1px 1px 2.5px 0px rgba(black, 0.5)
</style>