<template>
  <div id="app">
    <Header/>
    <word-input @search="searchWord"/>
    <word-definition :definition="wordDefinitions[0]" />
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import WordInput from '@/components/WordInput.vue'
import WordDefinition from '@/components/WordDefinition.vue'

export default {
  name: 'App',
  components: {
    Header,
    WordInput,
    WordDefinition,
  },
  data() {
    return {
      baseUrl: 'https://api.dictionaryapi.dev/api/v2/entries/en/',
      wordDefinitions: [],
      errorDetails: {},
    }
  },
  methods: {
    searchWord(word) {
      this.wordDefinitions = [];
      this.errorDetails = {};
      fetch(`${this.baseUrl}${word}`)
        .then((response) => {
          let status = response.ok;
          response.json().then((data) => {
            if (status) {
              this.wordDefinitions = data;
            } else {
              this.errorDetails = data;
            }
          })
        })
    },
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

:root {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 14px;
  line-height: 17px;
  font-weight: 400;
  --purple: #A445ED;
  --purple-alpha: #A445ED40;
  --red: #FF5252;
  --black-variant-1: #050505;
  --black-variant-2: #1F1F1F;
  --black-variant-3: #2D2D2D;
  --black-variant-4: #3A3A3A;
  --grey-variant-1: #757575;
  --grey-variant-2: #E9E9E9;
  --grey-variant-3: #F4F4F4;
  --grey-variant-transparent: #0000001A;
  --white: #FFFFFF;
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
  --shadow-color: var(--grey-variant-transparent);
  --input-bg: var(--grey-variant-3);
  --hr-color: var(--grey-variant-2);
}

:root[data-theme="dark"] {
  --body-background: var(--black-variant-1);
  --text-color: var(--white);
  --shadow-color: var(--purple);
  --input-bg: var(--black-variant-2);
  --hr-color: var(--black-variant-4);
}

body {
  background-color: var(--body-background);
  color: var(--text-color);
  transition: 0.3s ease-in-out;
}

#app {
  width: 100%;
  max-width: 780px;
  margin: 0 auto;
  padding: 50px 40px;
  box-sizing: border-box;
}

@media screen and (max-width: 570px) {
  :root {
    font-size: 12px;
    line-height: 16px;
  }
  
  #app {
    padding: 30px 25px;
  }
}
</style>
