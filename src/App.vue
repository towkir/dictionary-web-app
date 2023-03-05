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

:root,
:root[data-font="sans-serif"] {
  font-family: 'Inter', sans-serif;
}

:root[data-font="serif"] {
  font-family: 'Lora', serif;
}

:root[data-font="monospace"] {
  font-family: 'Inconsolata', monospace;
}

:root,
:root[data-theme="light"] {
  --body-background: var(--white);
  --text-color: var(--black-variant-1);
}

:root[data-theme="dark"] {
  --body-background: var(--black-variant-1);
  --text-color: var(--white);
}

body {
  background-color: var(--body-background);
  color: var(--text-color);
  transition: 0.3s ease-in-out;
}

#app {
  width: 780px;
  margin: 60px auto;
}
</style>
