<script>
  import axios from 'axios'

  export default {
    created() {
      axios.get('https://fakestoreapi.com/products').then((response) => {
        this.products = response.data
        console.log(response.data)
      })
    },

    data() {
      return {
        products: null
      }
    },
    methods: {
      onClickPlus() {
        this.countUpButton = this.countUpButton + 1
      }
    }
  }
</script>

<template>
  <ul class="gridLayoutContainer">
    <li :key="product.id" v-for="product in products">
      <div
        class="card"
        style="width: 15em; min-height: 31rem; margin-top: 4rem"
      >
        <img :src="product.image" class="card-img-top" alt="" />
        <div class="card-body">
          <h5 class="card-title">{{ product.title }}</h5>
          <p class="card-text">
            $ {{ product.price }}, Product id: {{ product.id }}
          </p>
          <input
            type="button"
            value="Add to cart"
            @click="$store.commit('addToCart', product)"
          />
        </div>
      </div>
    </li>
  </ul>
</template>

<style lang="scss">
  $cardColor: #f3e3d5;
  $textColor: #443c36;
  .gridLayoutContainer {
    display: grid;
    grid-template-columns: auto auto auto auto;
  }
  .card {
    background-color: $cardColor;
  }
  .card-body {
    margin-top: 2rem;
  }
  body {
    font-family: sans-serif;
  }
  ul {
    list-style-type: none;
    text-align: center;
  }
  img {
    height: 15rem;
    margin-top: 1rem;
  }
</style>
