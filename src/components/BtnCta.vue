<script setup>
defineProps({
  text: {
    type: String,
    required: true
  }
})
</script>

<template>
  <button class="btn link--shadow">{{ text }}</button>
</template>

<style scoped lang="scss">
  .btn {
    cursor: pointer;
    border-radius: 4px;
    background-color: var(--primary);
    color: #fff;
    grid-column: 1/3;
    padding: 16px 0;
    text-align: center;
  }
</style>