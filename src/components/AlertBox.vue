<script setup>
import Warning from '../assets/image/warning.svg'
defineProps({
  text: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="box grid--column font--size--m">
    <img :src="Warning" alt="Warning"> {{ text }}
  </div>
</template>

<style lang="scss">
  .box {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    border-radius: 4px;
    border: 1px solid var(--warning);
    background-color: var(--warning-light);
    padding: 16px;
  }
</style>
