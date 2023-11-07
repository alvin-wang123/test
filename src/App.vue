<script setup>
import { gsap } from 'gsap'
console.log(gsap)
</script>

<template>
  <header></header>

  <main>
    <div class="title-group">
      <h1>welcomewelcomewelcomewelcome</h1>
      <h2>apple</h2>
      <h3>banana</h3>
    </div>
  </main>
</template>

<style scoped lang="scss">
main {
  .title-group {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translateX(-50%);
    h1 {
      margin-bottom: 100px;
    }
    h2 {
      margin-bottom: 100px;
    }
    h3 {
    }
  }
}
</style>
