<template>
  <div id="background">
    <img id="background-img" src="/images/background.jpg">
    <div id="overlay"></div>
    <div id="mouses">
      <img src="/images/mouse_alive_white.png" id="mouse-1">
      <img src="/images/mouse_alive_white.png" id="mouse-2">
      <img src="/images/mouse_alive_white.png" id="mouse-3">
      <img src="/images/mouse_alive_white.png" id="mouse-4">
      <img src="/images/mouse_dead_white.png" id="mouse-5">
      <img src="/images/mouse_dead_white.png" id="mouse-6">
      <img src="/images/mouse_dead_white.png" id="mouse-7">
      <img src="/images/mouse_dead_white.png" id="mouse-8">
      <img src="/images/mouse_dead_white.png" id="mouse-9">
      <img src="/images/mouse_alive_white.png" id="mouse-10">
      <img src="/images/mouse_dead_white.png" id="mouse-11">
      <img src="/images/mouse_alive_white.png" id="mouse-12">
    </div>
  </div>
</template>

<style lang="sass" scoped>
#background
  #background-img
    position: absolute
    width: 100vw
    height: 100vh
    object-fit: cover
    z-index: 1
    filter: blur(1px)
    -webkit-filter: blur(1px)

  #overlay
    position: absolute
    width: 100vw
    height: 100vh
    background: black
    opacity: 0.9
    z-index: 2

  #mouses
    position: absolute
    width: 100vw
    height: 100vh
    z-index: 3
    overflow: hidden

    img
      position: absolute
      width: 75px
      object-fit: cover
      opacity: 0.15
      filter: blur(2px)
      -webkit-filter: blur(2px)

    #mouse-1
      left: 63vw
      top: 26vh
      transform: rotateZ(38deg)

    #mouse-2
      left: 19vw
      top: 20vh
      transform: rotateZ(-38deg)

    #mouse-3
      left: 59vw
      top: 63vh
      transform: rotateZ(64deg)

    #mouse-4
      left: 7vw
      top: 80vh
      transform: scaleX(-1) rotateZ(18deg)

    #mouse-5
      left: 30vw
      top: 3vh
      transform: rotateZ(-58deg)

    #mouse-6
      left: 10vw
      top: 62vh
      transform: rotateZ(-158deg)

    #mouse-7
      left: 37vw
      top: 73vh
      transform: rotateZ(-78deg)

    #mouse-8
      left: 78vw
      top: 7vh
      transform: rotateZ(32deg)

    #mouse-9
      left: 5vw
      top: 40vh
      transform: rotateZ(-62deg)

    #mouse-10
      left: 65vw
      top: 83vh
      transform: rotateZ(76deg)

    #mouse-11
      left: 86vw
      top: 47vh
      transform: rotateZ(66deg)

    #mouse-12
      left: -5vw
      top: 10vh
      transform: scaleX(-1) rotateZ(-36deg)
</style>