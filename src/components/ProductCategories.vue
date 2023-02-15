<script>
  import axios from 'axios'

  export default {
    created() {
      axios
        .get(
          'https://fakestoreapi.com/products/category/' +
            this.$route.params.anyCategory
        )
        .then((response) => {
          this.products = response.data
          console.log(response.data)
        })
    },
    data() {
      return {
        products: null
      }
    }
  }
</script>

<template>
  <h1>{{ $route.params.anyCategory }}</h1>
  <div class="container">
    <ul>
      <li :key="product.id" v-for="product in products">
        <img alt="" :src="product.image" />
        {{ product.title }} , Price: {{ product.price }} $ Description:
        {{ product.description }} What did others think about this product?
        {{ product.rating.count }} people rated this product
        {{ product.rating.rate }} /5
        <input
          type="button"
          value="Add to cart"
          @click="$store.commit('addToCart', product)"
        />
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
  $a-color: rgb(255, 255, 255);
  div {
    font-family: sans-serif;
    background-color: $a-color;
  }

  ul {
    list-style-type: none;
    text-align: center;
  }
  img {
    height: 15rem;
  }
</style>
