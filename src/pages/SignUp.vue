<script setup>
import { reactive, ref } from 'vue' 
import NavLink from '../components/NavLink.vue';
import AlertBox from '../components/AlertBox.vue'
import BtnThirdParty from '../components/BtnThirdParty.vue';
import FormRegular from '../components/FormRegular.vue'
import FormPassword from '../components/FormPassword.vue'
import BtnCta from '../components/BtnCta.vue';
// image
import IconGoogle from '../assets/image/IconGoogle.vue';
import IconFB from '../assets/image/IconFB.vue';
defineProps({
  msg: {
    type: String,
    required: true
  }
})
const formDate = reactive({
  firstname: '',
  firstnameCompleted: true,
  lastname: '',
  lastnameCompleted: true,
  email: '',
  emailCompleted: true,
  password: '',
  passwordCompleted: true,
  terms: false
})
const checkForm = ref(true)
const sendForm = () => {
  formDate.firstnameCompleted = formDate.firstname !== ""
  formDate.lastnameCompleted = formDate.lastname !== ""
  formDate.emailCompleted = formDate.email !== ""
  formDate.passwordCompleted = formDate.password !== ""
  checkForm.value = formDate.firstnameCompleted && formDate.lastnameCompleted && formDate.emailCompleted && formDate.passwordCompleted && formDate.terms
}
</script>

<template>
  <div class="container">
    <NavLink text="← Back" />
    <div class="wrap">
      <div class="title grid--column">
        <p class="title--sub">Start from free</p>
        <p class="title--main">Create an account</p>
      </div>
      <AlertBox v-if="!checkForm" text="Please complete all the required fields to proceed." />
      <BtnThirdParty msg="Sign up with Google"><IconGoogle/></BtnThirdParty>
      <BtnThirdParty msg="Sign up with Facebook"><IconFB/></BtnThirdParty>
      <div class="line grid--column">
        <span class="line--text">Or use your email for registration</span>
      </div>
      <FormRegular title="First Name" inputName="firstname" 
        @updateVal="e => formDate.firstname = e"
        :completed="formDate.firstnameCompleted" />
      <FormRegular title="Last Name" inputName="lastname" 
        @updateVal="e => formDate.lastname = e"
        :completed="formDate.lastnameCompleted" />
      <FormRegular title="E-mail" inputName="email" 
        @updateVal="e => formDate.email = e"
        :completed="formDate.emailCompleted" className="grid--column"/>
      <FormPassword title="Password" inputName="password" 
        @updateVal="e => formDate.password = e"
        :completed="formDate.passwordCompleted" className="grid--column"/>
      <label class="terms grid--column font--size--s" for="terms">
        <input class="terms--input" type="checkbox" id="terms" v-model="formDate.terms">
        <div class="terms--input--box">
          <svg :class="formDate.terms ? 'display--block' : 'display--none'" width="11" height="9" viewBox="0 0 11 9" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.5 0L11 1.25L4.5 8.75L0 4.25L1.375 2.875L4.375 5.875L9.5 0Z" fill="#3C71FF"/>
          </svg>
        </div>
        <span>By creating account, you agree to accept our Privacy Policy, Terms of Service and Notification settings.</span>
      </label>
      <BtnCta text="Create an Free Account!" @click="sendForm" />
      <div class="grid--column font--size--s font--center">
        Already have an account?
        <a class="link--primary link--underline" href="#">Log in</a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  .container {
    padding: 24px 8px;
    width: 100%;
    background-color: #fff;
    border-radius: 4px;
    display: flex;
    align-items: center;
    flex-direction: column;
    @media (min-width: 768px) {
      margin: 16px auto;
      width: 610px;
    }
  }
  .wrap {
    width: 100%;
    display: grid;
    gap: 16px 20px;
    grid-template-columns: 1fr 1fr;
    @media (min-width: 768px) {
      width: 400px;
    }
  }
  .title {
    &--sub {
      font-size: 18px;
      padding-bottom: 8px;
    }
    &--main {
      font-size: 30px;
      font-weight: 700;
    }
  }
  .line {
    position: relative;
    margin-bottom: 8px;
    &--text {
      position: relative;
      z-index: 10;
      background-color: #fff;
      padding-right: 8px;
    }
    &::after {
      content: '';
      position: absolute;
      left: 0;
      top: 50%;
      width: 100%;
      height: 1px;
      background: #000;
    }
  }
  .terms {
    cursor: pointer;
    display: grid;
    grid-template-columns: 18px 1fr;
    align-items: center;
    gap: 8px;
    color: var(--third);
    &--input {
      display: none;
      &--box {
        height: 18px;
        background-color: var(--grey);
        border-radius: 2px;
        display: flex;
        justify-content: center;
        align-items: center;
      }
      &:checked + div {
        background-color: #fff;
        border: 1px solid var(--primary);
      }
    }
  }
</style>