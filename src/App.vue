<template>
  <div class="container" id="app">
    <Timer />
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

export default {
  name: 'App',
  components: {
    Timer
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #929496;
  margin-top: 60px;
}

body {
  background: #2c3e50;
}
</style>
