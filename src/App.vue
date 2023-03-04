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
:root {
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 14px;
  line-height: 17px;
  font-weight: 400;
}

:root[font-family="serif"] {
  font-family: 'Lora', serif;
}

:root[font-family="monospace"] {
  font-family: 'Inconsolata', monospace;
}

#app {
  width: 780px;
  margin: 60px auto;
}
</style>
