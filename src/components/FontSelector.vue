<template>
  <div class="font-selector">
    <div
      class="selected-font"
      @click="toggleFontPicker"
    >
      {{ selectedFont.label }}
      <img src="@/assets/images/icon-arrow-down.svg" class="icon-dropdown"/> 
    </div>
    <div
      v-if="fontPickerOpen"
      class="font-options"
    >
      <span
        v-for="font in fontOptions"
        :key="font.value"
        :class="font.value"
        @click="chooseFont(font)"
      >
        {{font.label}}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FontSelector',
  data() {
    return {
      selectedFont: {
        label: 'Sans Serif',
        value: 'sans-serif',
      },
      fontOptions: [
        { label: 'Sans Serif', value: 'sans-serif' },
        { label: 'Serif', value: 'serif' },
        { label: 'Mono', value: 'monospace' },
      ],
      fontPickerOpen: false,
    }
  },
  methods: {
    toggleFontPicker() {
      this.fontPickerOpen = !this.fontPickerOpen;
    },
    applyFont(font) {
      document.documentElement.setAttribute('data-font', font);
    },
    chooseFont(font) {
      this.selectedFont = font;
      this.applyFont(font.value);
      this.fontPickerOpen = false;
    },
  }
}
</script>

<style>
.font-selector {
  cursor: pointer;
  position: relative;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}

.font-selector .selected-font {
  font-size: 1.26rem;
  line-height: 1.68rem;
  font-weight: 700;
}

.font-selector .selected-font .icon-dropdown {
  margin-left: 15px;
}

.font-selector .font-options {
  position: absolute;
  background-color: var(--body-background);
  transition: 0.3s ease-in-out;
  width: 180px;
  top: calc(100% + 18px);
  right: 0;
  box-shadow: 0 5px 30px var(--shadow-color);
  border-radius: 16px;
  padding: 12px 0;
}
.font-selector .font-options span {
  display: block;
  width: 100%;
  box-sizing: border-box;
  font-size: 1.26rem;
  font-weight: 700;
  padding: 12px 24px;
}

.font-selector .font-options span:hover {
  color: var(--purple);
}

.font-selector .font-options span.sans-serif {
  font-family: 'Inter', sans-serif;
}

.font-selector .font-options span.serif {
  font-family: 'Lora', serif;
}

.font-selector .font-options span.monospace {
  font-family: 'Inconsolata', monospace;
}
</style>
