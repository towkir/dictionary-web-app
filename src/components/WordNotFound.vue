<template>
  <div v-if="message.title" class="message-wrapper">
    <h1>😕</h1>
    <h3>{{message.title}}</h3>
    <p>{{message.message}}</p>
    <p>{{message.resolution}}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: Object,
    }
  },
}
</script>

<style>
.message-wrapper {
  text-align: center;
}

.message-wrapper h1 {
  font-size: 4.48rem;
  line-height: 5.25rem;
  margin-bottom: 30px;
}

.message-wrapper h3 {
  font-size: 1.4rem;
  line-height: 1.82rem;
  margin-bottom: 15px;
}
.message-wrapper p {
  font-size: 1.26rem;
  line-height: 1.68rem;
  color: var(--grey-variant-1);
}
</style>
