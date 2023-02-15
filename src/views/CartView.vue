<script>
  import TheCart from '../components/TheCart.vue'
  export default {
    components: {
      TheCart
    }
    // data() {
    //   return { temp: 'copy right' } ändrar prop
    // }
  }
</script>

<template>
  <!-- <TheCart :copy="temp" /> -->
  <TheCart copy="Copy right: The online Bazar 2023" />
</template>
