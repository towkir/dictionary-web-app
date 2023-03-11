<template>
  <div class="input-wrapper">
    <input
      type="text"
      placeholder="Search for any word..."
      v-model="word"
      :class="{ error: attemptedEmptySearch }"
      @keypress="validateWordAndSearch"
    />
    <div class="placeholder">
      <span v-if="attemptedEmptySearch" class="error">Whoops, can't be empty…</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'WordInput',
  data() {
    return {
      word: '',
      attemptedEmptySearch: false,
    }
  },
  methods: {
    validateWordAndSearch(event) {
      this.attemptedEmptySearch = false;
      if (event.keyCode === 13) {
        this.attemptedEmptySearch = !this.word.length;
        if (!this.attemptedEmptySearch) {
          this.$emit('search', this.word);
        }
      }
    }
  }
}
</script>

<style>
.input-wrapper {
  margin-bottom: 15px;
}

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
  margin-bottom: 10px;
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

.input-wrapper input[type="text"].error {
  border-color: var(--red);
}

.input-wrapper .placeholder {
  min-height: 20px;
}

.input-wrapper span.error {
  color: var(--red);
}
@media screen and (max-width: 570px) {
  .input-wrapper input[type="text"] {
    padding: 16px 24px;
  }
}
</style>
