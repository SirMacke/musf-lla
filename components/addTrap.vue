<template>
  <div id="addTrap">
    <div id="box">
      <h2>Lägg Till Musfälla</h2>
      <form onsubmit="return false">
        <input type="text" v-model="trapName" placeholder="Namn...">
        <button type="submit" @click="addTrap">Ok</button>
      </form>  
    </div>
  </div>
</template>

<script setup>
let trapName = useState('trapName', () => '');

function addTrap() {
  closeAddTrap();
}

function closeAddTrap() {
  let addTrapActive = useState('addTrapActive');
  addTrapActive.value = false;
}
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
      margin: 0px 30px 40px 30px

      input
        border: none
        border-radius: 5px
        height: 45px
        padding: 0px 12.5px
        font-size: 1em
        width: calc(100% - 25px)

        &:focus
          outline: none

      button
        position: absolute
        height: 45px
        width: 45px
        right: 30px
        background: $color-3
        border: none
        border-radius: 5px
        transition: 0.25s
        color: $white-2

        &:hover
          cursor: pointer
          background: $color-4

</style>