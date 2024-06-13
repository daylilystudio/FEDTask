<script setup>
import { ref } from 'vue' 
import CheckText from '../components/CheckText.vue'
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
const open = ref(false)
const checkMin = ref(false)
const checkNumber = ref(false)
const enterPassword = (e) => {
  checkMin.value = e.target.value.length>=8
  checkNumber.value = /[0-9]/.test(e.target.value)
  emits('updateVal', e.target.value)
}
</script>

<template>
  <label :class="className" class="input" :for="inputName">
    <input :type="open ? 'text' : 'password'" :name="inputName" :id="inputName" v-model="data" @input="enterPassword" class="input--box" required="required">
    <span class="input--title">{{ title }}</span>
    <span v-if="!completed" class="input--warning" />
    <div class="eye" @click="open=!open">
      <img src="../assets/image/eye_view.svg" alt="view" v-if="open">
      <img src="../assets/image/eye_hide.svg" alt="hide" v-if="!open">
    </div>
  </label>
  <div class="adjust grid--column">
    <CheckText text="8 Characters min." :check="checkMin" />
    <CheckText text="One number" :check="checkNumber" />
  </div>
</template>

<style lang="scss">
  .eye {
    cursor: pointer;
    position: absolute;
    right: 14px;
    top: 50%;
    transform: translateY(-50%);
  }
  .adjust{
    margin-top: -8px;
    display: flex;
    gap: 14px;
  }
</style>