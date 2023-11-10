<script setup>
import { gsap } from 'gsap'
import { ref, onMounted, onUnmounted } from 'vue'
import catIcon from './assets/catIcon.vue'
let main = ref(null)
let ctx
let tl
function removeElement(element) {
  if (typeof element === 'string') {
    element = document.querySelector(element)
  }
  return function () {
    element.parentNode.removeChild(element)
  }
}
onMounted(() => {
  ctx = gsap.context(() => {
    tl = gsap
      .timeline()
      .to('.cat-icon', { rotate: 360, repeat: 1 })
      .to('.cat-icon', { opacity: 0, duration: 0.5 })
      // .remove('.cat-icon')
      .call(removeElement('.cat-icon'))
      .to('.welcome', { opacity: 1, duration: 1, y: 0, delay: 0.5 })
      .to('.h2', { opacity: 1, duration: 1, y: 0 })
      .to('.h3', { opacity: 1, duration: 1, y: 0 })
  }, main.value)
  // tween = gsap.to('.welcome', { opacity: 1, duration: 1, y: 0 }, main.value)
})
onUnmounted(() => {
  ctx.revert()
})

const test = () =>
  fetch('https://jsonplaceholder.typicode.com/todos/1')
    .then((response) => response.json())
    .then((json) => console.log(json))
</script>

<template>
  <header></header>
  <div class="box green"></div>
  <main ref="main">
    <catIcon class="cat-icon" />
    <div class="title-group">
      <h1 class="welcome" @click="test">welcomewelcomewelcomewelcome</h1>
      <h2 class="h2">apple</h2>
      <h3 class="h3">banana</h3>
    </div>
  </main>
</template>

<style scoped lang="scss">
main {
  .green {
    display: block;
    background-color: green;
    width: 100px;
    height: 100px;
  }
  .cat-icon {
    width: 100vw;
    height: 100vh;
    background-color: white;
    position: fixed;
    z-index: 2;
    opacity: 1;
  }
  .title-group {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translateX(-50%);
    h1,
    h2,
    h3 {
      margin-bottom: 100px;
      opacity: 0;
      transform: translateY(30px);
    }
  }
}
</style>
