<template>
  <div id="addTrap">
    <div id="box">
      <h2>Lägg Till Musfälla</h2>
      <form>
        <input type="text" v-model="trapName" placeholder="Namn...">
        <button type="submit">_|</button>
      </form>  
    </div>
  </div>
</template>

<script setup>
let trapName = useState('trapName', () => '');
</script>

<style lang="sass" scoped>
#addTrap
  position: absolute
  width: 100vw
  height: 100vh
  background: rgba($color-1, 0.25)
  z-index: 100

  #box
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    width: 75vw
    height: auto
    background-color: $white-2
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px
    border-radius: 15px

    h2
      margin: 40px 35px 20px 35px
      color: $color-3

    form

      input
        margin: 0px 30px 40px 30px
        border: none
        border-radius: 5px
        padding: 13.5px 15px 11.5px 15px
        font-size: 1em
        width: calc(100% - 60px - 30px)

        &:focus
          outline: none

      button
        position: absolute
</style>