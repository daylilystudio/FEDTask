<script setup>
defineProps({
  check: {
    type: Boolean,
    required: true
  },
  text: {
    type: String,
    required: true
  }
})
</script>

<template>
  <span class="check font--size--xs" :class="check ? '' : 'font--grey'">
    <i class="check--tick" :class="check ? '' : 'bg--grey'">
      <svg width="7" height="6" viewBox="0 0 11 9" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M9.5 0L11 1.25L4.5 8.75L0 4.25L1.375 2.875L4.375 5.875L9.5 0Z" fill="#fff"/>
      </svg>
    </i>
    {{ text }}
  </span>
</template>

<style scoped lang="scss">
  .check {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    &--tick {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 11px;
      height: 11px;
      background-color: var(--deco);
      border-radius: 50%;
    }
  }
</style>