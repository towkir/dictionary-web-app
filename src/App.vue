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
  --purple: #A445ED;
  --red: #FF5252;
  --black-variant-1: #050505;
  --black-variant-2: #1F1F1F;
  --black-variant-3: #2D2D2D;
  --black-variant-4: #3A3A3A;
  --grey-variant-1: #757575;
  --grey-variant-2: #E9E9E9;
  --grey-variant-3: #F4F4F4;
  --white: #FFFFFF;
  --shadow-color: #0000001A;
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
