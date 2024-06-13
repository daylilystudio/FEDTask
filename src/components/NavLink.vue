<script setup>
defineProps({
  text: {
    type: String,
    required: true
  }
})
</script>

<template>
  <a href="#" class="link">
    <span class="link--underline">{{ text }}</span>
  </a>
</template>

<style scoped lang="scss">
  .link {
    margin-left: 16px;
    margin-bottom: 24px;
    width: 100%;
    @media (min-width: 768px) {
      margin-bottom: 32px;
      width: 550px;
    }
  }
</style>