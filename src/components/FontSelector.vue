<template>
  <div class="font-selector">
    <div
      class="selected-font"
      @click.stop="toggleFontPicker"
    >
      {{ selectedFont.label }}<svg class="icon-dropdown" xmlns="http://www.w3.org/2000/svg" width="14" height="8" viewBox="0 0 14 8"><path fill="none" stroke="#A445ED" stroke-width="1.5" d="m1 1 6 6 6-6"/></svg>
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
    hideFontPicker() {
      if (this.fontPickerOpen) {
        this.fontPickerOpen = false;
      }
    },
    applyFont(font) {
      document.documentElement.setAttribute('data-font', font);
      localStorage.setItem('dictionary-font', font);
    },
    chooseFont(font) {
      this.selectedFont = font;
      this.applyFont(font.value);
      this.fontPickerOpen = false;
    },
    getAppliedFont() {
      const appliedFont = localStorage.getItem('dictionary-font');
      let validFont;
      if (appliedFont) {
        validFont = this.fontOptions.find(item => item.value === appliedFont);
      }
      if (validFont) {
        this.chooseFont(validFont);
      }
    },
  },
  beforeMount() {
    this.getAppliedFont();
    window.addEventListener('click', this.hideFontPicker);
  },
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
