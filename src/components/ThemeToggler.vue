<template>
  <div class="theme-toggler">
    <label for="toggler-checkbox">
      <input
        type="checkbox"
        id="toggler-checkbox"
        v-model="darkThemeEnabled"
        @change="toggleTheme"
      >
      <span class="toggler">
        <span class="toggler-button"></span>
      </span>
    </label>
    <svg class="icon-moon" :class="{ active : darkThemeEnabled }" xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 22 22">
      <path fill="none" stroke="#838383" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M1 10.449a10.544 10.544 0 0 0 19.993 4.686C11.544 15.135 6.858 10.448 6.858 1A10.545 10.545 0 0 0 1 10.449Z"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'ThemeToggler',
  data() {
    return {
      darkThemeEnabled: false,
    }
  },
  methods: {
    toggleTheme() {
      const theme = this.darkThemeEnabled ? 'dark' : 'light';
      document.documentElement.setAttribute('data-theme', theme);
    },
  },
}
</script>

<style>
.theme-toggler {
  display: flex;
  align-items: center;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}

label[for="toggler-checkbox"] {
  line-height: 0;
}

label[for="toggler-checkbox"] input[type="checkbox"] {
  display: none;
}

label[for="toggler-checkbox"] input[type="checkbox"] + span.toggler {
  display: inline-block;
  position: relative;
  width: 40px;
  height: 20px;
  border-radius: 10px;
  background-color: var(--grey-variant-1);
  margin-right: 20px;
  cursor: pointer;
  transition: 0.3s ease-in-out;
}

label[for="toggler-checkbox"] input[type="checkbox"] + span.toggler span.toggler-button {
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  left: 3px;
  top: 3px;
  background-color: var(--white);
  transition: 0.3s ease-in-out;
}

label[for="toggler-checkbox"] input[type="checkbox"]:checked + span.toggler {
  background-color: var(--purple);
}

label[for="toggler-checkbox"] input[type="checkbox"]:checked + span.toggler span.toggler-button {
  left: 23px;
}

.theme-toggler svg.icon-moon.active path {
  stroke: var(--purple);
}

@media screen and (max-width: 570px) {
  label[for="toggler-checkbox"] input[type="checkbox"] + span.toggler {
    margin-right: 12px;
  }
}
</style>