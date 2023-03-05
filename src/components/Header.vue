<template>
  <div class="header">
    <img src="@/assets/images/logo.svg" />
    <div class="settings">
      <font-selector />
      <div class="vertical-separator"></div>
      <div class="theme-toggler">
        <input type="checkbox">
        <img src="@/assets/images/icon-moon.svg" />
      </div>
    </div>
  </div>
</template>

<script>
import FontSelector from './FontSelector.vue'
export default {
  components: { FontSelector },
  name: 'Header',
}
</script>

<style>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header .settings {
  display: flex;
  align-items: center;
}

.header .settings .vertical-separator {
  width: 1px;
  height: 34px;
  background-color: var(--grey-variant-2);
  margin: 0 25px;
}
</style>
