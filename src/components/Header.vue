<template>
  <div class="header">
    <img src="@/assets/images/logo.svg" />
    <div class="settings">
      <font-selector />
      <div class="vertical-separator"></div>
      <theme-toggler />
    </div>
  </div>
</template>

<script>
import FontSelector from '@/components/FontSelector.vue'
import ThemeToggler from '@/components/ThemeToggler.vue'
export default {
  components: { FontSelector, ThemeToggler },
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
