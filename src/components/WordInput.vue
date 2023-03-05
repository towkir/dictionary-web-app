<template>
  <div class="input-wrapper">
    <input
      type="text"
      placeholder="Search for any word..."
      v-model="word"
    />
  </div>
</template>

<script>
export default {
  name: 'WordInput',
  data() {
    return {
      word: '',
    }
  },
}
</script>

<style>
.input-wrapper input[type="text"] {
  appearance: none;
  font-family: inherit;
  border: 1px solid transparent;
  color: var(--text-color);
  background-color: var(--input-bg);
  caret-color: var(--purple);
  border-radius: 16px;
  transition: 0.3s ease-in-out;
  font-size: 1.4rem;
  font-weight: 700;
  padding: 20px 24px;
  background-image: url('~@/assets/images/icon-search.svg');
  background-repeat: no-repeat;
  background-position: calc(100% - 20px) center;
  display: block;
  box-sizing: border-box;
  width: 100%;
}

.input-wrapper input[type="text"]:focus {
  outline: none;
  border-color: var(--purple);
}
</style>