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
          <p>{{ devices.length }}</p>
        </div>
      </div>
      <div class="item">
        <h2>Fångade Möss</h2>
        <div>
          <img src="/images/mouse-trap-mouse-100.png" id="mouse-trap-closed">
          <p>{{ closeEvents.length }}</p>
        </div>
      </div>
    </main>
    <footer>
      <div id="addTrapButton" @click="changeAddTrapState">+</div>
      <a @click="logout()">Logout</a>
    </footer>
  </div>
</template>

<script setup>
const auth = useCookie('auth');
console.log('auth', auth);
if (auth == null || auth == undefined || auth.value == undefined || auth.value == '') await navigateTo('/login');

let devices = ref([]);
let closeEvents = ref([]);

findData();
setInterval(findData, 2000);

async function findData() {
  devices.value = JSON.parse(await $fetch('https://api.simsva.se/musfalla/devices', {
    method: 'GET',
    headers: {
      'Authorization': auth.value,
      'Content-Type': 'application/json'
    }
  }));

  console.log('devices', devices)


  closeEvents.value = JSON.parse(await $fetch('https://api.simsva.se/musfalla/events', {
    method: 'GET',
    headers: {
      'Authorization': auth.value,
      'Content-Type': 'application/json'
    }
  })).filter(n => n.type == 'close');

  console.log('closeEvents', closeEvents)
}

let addTrapActive = useState('addTrapActive', () => false);

function changeAddTrapState() {
  addTrapActive.value = !addTrapActive.value;
  console.log(addTrapActive);
}

async function logout() {
  auth.value = null;
  await navigateTo('/login');
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

@keyframes footerSlideFromBottom
  0%
    opacity: 0
    bottom: -50px
  100%
    opacity: 1
    bottom: 0px

footer
  position: absolute
  bottom: 0px
  width: 100%
  height: auto
  animation: footerSlideFromBottom ease-in-out 1s 1 1s forwards
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
    background: rgba(red, 0.25)
    border-radius: 5px
    box-shadow: rgba(red, 0.2) 0px 0px 8px

    &:hover
      background: rgba(red, 0.35)
      cursor: pointer
      box-shadow: 1px 1px 2.5px 0px rgba(black, 0.5)

  a
    position: absolute
    top: 50%
    transform: translateY(-50%)
    right: 30px
    text-decoration: none
    color: white

  a:hover
    text-decoration: underline
    cursor: pointer
</style>