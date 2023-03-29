<template>
  <div id="addTrap">
    <div class="box" v-if="trapId == undefined || trapId == ''">
      <h2>Lägg Till Musfälla</h2>
      <form onsubmit="return false">
        <input type="text" v-model="trapName" placeholder="Namn...">
        <button type="submit" @click="addTrap">Ok</button>
      </form>  
    </div>
    <div class="box" v-else>
      <h2>ID Till Musfälla</h2>
      <p>{{ trapId }}</p>
      <button id="id-button" @click="closeAddTrap">Done</button>
    </div>
  </div>
</template>

<script setup>
const auth = useState('auth');
console.log('auth', auth);

let trapName = useState('trapName', () => '');
let trapId = useState('trapId', () => '');

async function addTrap() {
  let res = await $fetch('https://api.simsva.se/musfalla/devices', {
    method: 'POST',
    body: {
      name: trapName.value
    },
    headers: {
      'Authorization': auth.value,
      'Content-Type': 'application/json'
    }
  });
  trapId.value = res;
}

function closeAddTrap() {
  trapId.value = '';
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

  .box
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    width: 75vw
    height: auto
    background-color: black
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px
    border-radius: 15px
    color: white

    h2
      margin: 40px 35px 20px 35px
      color: rgba(red, 0.5)

    p
      margin: 0px 35px
      word-break: break-all

    #id-button
      position: relative
      height: 45px
      width: 100px
      margin: 25px 35px 25px 35px
      background: rgba(red, 0.25)
      border: none
      border-radius: 5px
      transition: 0.25s
      color: $white-2

      &:hover
        cursor: pointer
        background: rgba(red, 0.35)

    form
      margin: 0px 30px 40px 30px

      input
        background: rgba(black, 0.1)
        border: none
        border-radius: 5px
        height: 45px
        padding: 0px 12.5px
        font-size: 1em
        color: white
        width: calc(100% - 25px)
      
        @media screen and (max-width: 800px)
          margin: 5px 0px

        input::placeholder
          color: rgba(white, 0.75)

        input:focus
          outline: 2.5px solid rgba($white-2, 0.25)

      button
        position: absolute
        height: 45px
        width: 45px
        right: 30px
        background: rgba(red, 0.25)
        border: none
        border-radius: 5px
        transition: 0.25s
        color: $white-2
        margin-top: 5px

        &:hover
          cursor: pointer
          background: rgba(red, 0.35)

</style>