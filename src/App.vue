<template>
  <div id="app">
    <Header/>
    <word-input />
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import WordInput from '@/components/WordInput.vue'

export default {
  name: 'App',
  components: {
    Header,
    WordInput,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 780px;
  margin: 60px auto;
}
</style>
