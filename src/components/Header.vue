<template>
  <div class="header">
    <img src="@/assets/images/logo.svg" />
    <div class="settings">
      <div class="font-selector">
        Sans Serif
        <img src="@/assets/images/icon-arrow-down.svg"/> 
      </div>
      <div class="vertical-separator"></div>
      <div class="theme-toggler">
        <input type="checkbox">
        <img src="@/assets/images/icon-moon.svg" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
