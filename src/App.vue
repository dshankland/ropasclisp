<template>
  <div id="app">
    <RockPaperScissorsLizardSpock/>
  </div>
</template>

<script>
import RockPaperScissorsLizardSpock from './components/RockPaperScissorsLizardSpock.vue'

export default {
  name: 'app',
  components: {
    RockPaperScissorsLizardSpock
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
