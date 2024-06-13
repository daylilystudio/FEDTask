<script setup>
import { ref } from 'vue' 
defineProps({
  title: {
    type: String,
    required: true
  },
  inputName: {
    type: String,
    required: true
  },
  className: {
    type: String
  },
  completed: {
    type: Boolean,
    required: true
  }
})
const emits = defineEmits(['updateVal'])
const data = ref('')
</script>

<template>
  <label :class="className" class="input" :for="inputName">
    <input type="text" :name="inputName" :id="inputName" v-model="data" @input="emits('updateVal', data)" class="input--box" required="required">
    <span class="input--title">{{ title }}</span>
    <span v-if="!completed" class="input--warning" />
  </label>
</template>