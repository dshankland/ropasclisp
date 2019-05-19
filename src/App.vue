<template>
  <div id="app">
    <Header/>
    <RockPaperScissorsLizardSpock/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import RockPaperScissorsLizardSpock from '@/components/RockPaperScissorsLizardSpock.vue'

export default {
  name: 'app',
  components: {
    RockPaperScissorsLizardSpock,
    Header
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
