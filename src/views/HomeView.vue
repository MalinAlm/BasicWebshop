<script>
  export default {
    data() {
      return { searchText: null }
    },
    watch: {
      searchText(old, newValue) {
        console.log(old + ' ' + newValue)
      }
    }
  }
</script>

<template>
  <div id="writeSomething">
    <p>Write something, and have a look in the console.</p>
    <input v-model="searchText" />
  </div>
  <h1>Categories</h1>
  <div id="categoryContainer">
    <RouterLink to="/category/jewelery?">
      <img src="/assets/jewelry.jpg" alt="Jewelry" />
    </RouterLink>
    <RouterLink to="/category/men's clothing">
      <img src="/assets/kläder.jpg" alt="Men Clothing" />
    </RouterLink>
    <RouterLink to="/category/women's clothing">
      <img src="/assets/kläder2.jpg" alt="Women Clothing" />
    </RouterLink>
    <RouterLink to="/category/electronics">
      <img src="/assets/elektronik2.jpg" alt="Electronics" />
    </RouterLink>
  </div>
  <!-- <img src="/assets/kläder2.jpg" alt="Women Clothing" />
  <img src="/assets/elektronik2.jpg" alt="Electronics" /> -->
</template>

<style scoped>
  #categoryContainer {
    display: flex;
    justify-content: space-evenly;
    margin-top: 7rem;
  }
  img {
    border-radius: 7%;
  }
  #writeSomething {
    display: flex;
    justify-content: center;
    margin-top: 7rem;
  }
  h1 {
    margin-top: 3rem;
    text-align: center;
  }
</style>
