<script>
  export default {
    data() {
      return {
        signUpName: null,
        signUpEmail: null,
        thankYouMsg: null
      }
    },
    emits: ['on-sign-up'],
    methods: {
      onSubmit(event) {
        event.preventDefault()

        this.thankYouMsg = `Tack, ${this.signUpName}`
        this.signUpName = null
        this.$emit('on-sign-up')
      }
    }
  }
</script>
<template>
  <p>Sign up to our newsletter:</p>
  <label for="signUpName">
    name
    <input name="Name" id="signUpName" v-model="signUpName" />
  </label>
  <label for="signUpEmail">
    email
    <input name="Email" id="signUpEmail" v-model="signUpEmail" />
  </label>

  <input
    :disabled="signUpName === null"
    type="button"
    @click="onSubmit"
    value="Sign me up!"
  />
  <p v-if="thankYouMsg !== null">{{ thankYouMsg }}</p>
</template>
