<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <a class="font--size--s link link--shadow" href="#">
    <slot></slot>
    {{ msg }}
  </a>
</template>

<style scoped lang="scss">
  .link {
    padding: 16px 0 16px 12px;
    border: 1px solid var(--primary);
    border-radius: 4px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
</style>