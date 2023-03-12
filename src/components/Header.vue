<template>
  <div class="header">
    <img src="@/assets/images/logo.svg" class="logo" alt="logo" />
    <div class="settings">
      <font-selector />
      <div class="vertical-separator"></div>
      <theme-toggler />
    </div>
  </div>
</template>

<script>
import FontSelector from '@/components/FontSelector.vue';
import ThemeToggler from '@/components/ThemeToggler.vue';
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
  margin-bottom: 50px;
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

@media screen and (max-width: 570px) {
  .header {
    margin-bottom: 30px;
  }

  .header img.logo {
    max-width: 28px;
  }

  .header .settings .vertical-separator {
    margin: 0 16px;
  }
}
</style>
