<script>
  import SignUpNews from '../components/SignUpNews.vue'

  export default {
    components: {
      SignUpNews
    },

    methods: {
      newsLetter() {
        alert('Tack, vad kul att du vill ta del av vårt nyhetsbrev!')
      }
    }
  }
</script>

<template>
  <SignUpNews @on-sign-up="newsLetter" />
  <!-- <input v-model="signUpName" /> -->
</template>
