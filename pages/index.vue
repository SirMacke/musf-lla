<template>
  <div>
    <background />
    <addTrap v-if="addTrapActive" />
    <h1 id="h1">Musfälla</h1>
    <main>
      <div class="item">
        <h2>Aktiva Fällor</h2>
        <div>
          <img src="/images/mouse-trap-100.png" id="mouse-trap-open">
          <p>3</p>
        </div>
      </div>
      <div class="item">
        <h2>Fångade Möss</h2>
        <div>
          <img src="/images/mouse-trap-mouse-100.png" id="mouse-trap-closed">
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
  top: 15%
  margin: 0px auto
  left: 50%
  transform: translateX(-50%)
  font-size: 4em
  z-index: 3
  color: $white-2
  text-shadow: 2px 7px 5px rgba(red,0.15), 0px -4px 10px rgba(red,0.3)

main
  display: grid
  grid-template-rows: 1fr 1fr
  position: absolute
  left: 50%
  top: 52.5%
  transform: translate(-50%, -50%)
  background: rgba($color-1, 0.25)
  box-shadow: 0px 0px 1000px 10px rgba($color-1, 0.5)
  border-radius: 1000px
  padding: 25px
  color: $white-2
  z-index: 3

  .item
    display: flex
    flex-direction: column
    margin: 30px

    h2
      font-family: "Poppins", "sans-serif"
      margin: 0px 0px 30px 0px
      text-align: center
      width: 250px
      font-size: 1.75em

    div
      position: relative
      display: grid
      grid-template-columns: 1fr 1fr
      width: 200px
      left: 50%
      transform: translateX(-50%)
      

      img
        position: relative
        left: 50%
        top: 50%
        height: 80px
        width: 80px
        object-fit: cover
        filter: invert(100%)
        transform: translate(-50%, -50%) rotateZ(-10deg)

      p
        position: relative
        margin: auto
        font-size: 2em
        font-weight: bold

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
  z-index: 3

  #addTrapButton
    position: relative
    left: 25px
    bottom: 25px
    padding: 10px 22.5px
    text-decoration: none
    color: $white-2
    font-size: 2.5em
    background: rgba(red, 0.2)
    border-radius: 5px
    box-shadow: rgba(red, 0.2) 0px 0px 8px

    &:hover
      background: rgba($color-3, 0.35)
      cursor: pointer
      box-shadow: 1px 1px 2.5px 0px rgba(black, 0.5)
</style>