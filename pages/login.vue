<template>
  <div>
    <div id="login">
      <form onsubmit="return false">
        <h1>Login</h1>
        <div class="line"></div>
        <input type="text" autocomplete="off" v-model="usernameOrEmail" placeholder="Username or Email" />
        <input type="password" autocomplete="off" v-model="password" placeholder="Password" />
        <div id="bottom">
          <button @click="submitForm()">Submit</button>
          <p v-if="formWarning" class="warning">Please fill out all fields</p>
          <p v-if="formFailed" class="failed">Login failed</p>
        </div>
      </form>
      <footer>
        <NuxtLink to="/signup">Signup</NuxtLink>
      </footer>
    </div>
  </div>
</template>

<script setup>
let usernameOrEmail = '';
let password = '';

let formWarning = useState('formWarning', () => false);
let formFailed = useState('formFailed', () => false);
let working = false;

async function submitForm() {
  if (working) return;

  working = true;
  setTimeout(() => working = false, 3000);

  formWarning.value = false;
  formFailed.value = false;

  let res;
  try {
    if (usernameOrEmail == '' || password == '') res = { status: 400 };
    else {
      res = await $fetch('/api/login', {
        method: 'POST',
        body: {
          usernameOrEmail: usernameOrEmail,
          password: password
        }
      });
      useState('auth', () => res.auth);
    }
  } catch (err) {
    res = { status: 500 }
  }

  if (res.status == 200) return navigateTo('/');
  else if (res.status == 400) formWarning.value = true;
  else formFailed.value = true;
}
</script>

<style lang="sass" scoped>
#login
  position: relative
  height: 100vh
  width: 100vw
  z-index: 15

  @keyframes contactFadeUp
    0%
      opacity: 0
      top: 55%
    100%
      opacity: 1
      top: 50%

  form
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    width: auto
    height: auto
    display: flex
    flex-direction: column
    width: 600px
    animation: contactFadeUp ease-in-out 1s 1 0.8s forwards
    opacity: 0

    @media screen and (max-width: 1000px)
      width: 60%

    @media screen and (max-width: 800px)
      width: 70%

    @media screen and (max-width: 600px)
      width: 80%

    h1
      color: $color-7
      text-align: left
      position: relative
      top: 50%
      transform: translateY(-50%)
      font-size: 2.5em
      margin: 0px
      
      @media screen and (max-width: 800px)
        font-size: 2em
      
      @media screen and (max-width: 400px)
        font-size: 1.75em
    
    .line
      position: relative
      width: 105%
      left: 50%
      transform: translateX(-50%)
      height: 2px
      background: $color-5
      backdrop-filter: blur(10px)
      margin: 0px 0px 15px 0px

      @media screen and (max-width: 800px)
        margin: 0px 0px 10px 0px

    input
      background: rgba(black, 0.1)
      border: none
      border-radius: 5px
      height: 50px
      width: calc(100% - 35px)
      margin: 7.5px 0px
      padding: 0px 17.5px
      font-size: 1em
      color: black
      
      @media screen and (max-width: 800px)
        margin: 5px 0px

    input::placeholder
      color: rgba(black, 0.75)

    input:focus
      outline: 2.5px solid rgba($white-2, 0.1)

    #bottom
      position: relative
      display: flex
      flex-direction: row
      width: 100%
      margin-top: 15px

      @media screen and (max-width: 1200px)
        flex-direction: column

      @media screen and (max-width: 800px)
        margin-top: 10px

      button
        position: relative
        font-size: 1.1em
        border: none
        transition: 0.25s
        background-color: $color-6
        backdrop-filter: blur(10px)
        color: $white-2
        border-radius: 5px
        margin: 0px 0px 0px 0px
        padding-top: 3px
        width: 150px
        height: 50px

        @media screen and (max-width: 1200px)
          left: 50%
          transform: translateX(-50%)

        @media screen and (max-width: 400px)
          font-size: 1.1em
          width: 150px
          height: 45px

      button:hover
        cursor: pointer
        background-color: $color-7

      p
        position: absolute
        right: 5px
        text-align: right
        top: 50%
        transform: translateY(-50%)
        margin: auto 0px
        font-weight: bold

        @media screen and (max-width: 1200px)
          position: relative
          left: 50%
          transform: translateX(-50%)
          text-align: center
          margin-top: 20px

      .success
        color: $color-3

      .warning
        color: orange

      .failed
        color: red

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