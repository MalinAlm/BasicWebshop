<script>
  export default {
    props: {
      copy: { type: String, required: true }
    },

    data() {
      return {
        countUpButton: 0,
        firstName: '',
        lastName: '',
        email: '',
        phone: '',
        shopName1: 'The',
        shopName2: 'online',
        shopName3: 'bazar'
      }
    },

    methods: {
      onSubmit() {
        alert('Tack, för din beställning!')
      },
      onClickPlus() {
        this.countUpButton = this.countUpButton + 1
      },
      onClickMinus() {
        this.countUpButton = this.countUpButton - 1
        // this.copy = 'hej' en prop får ej ändras från koden
      }
    },

    computed: {
      shopName() {
        return `${this.shopName1} ${this.shopName2} ${this.shopName3}`
      }
    }
    // FOLLOWING CODE theTotal() IS FROM : https://stackoverflow.com/questions/51709425/how-to-get-total-to-display-on-vue-component-from-vuex-store
    // computed: {
    //   theTotal() {
    //     $store.state.cart.reduce((result, product) => {
    //       // We need to ensure that the property is of the type Number.
    //       result += Number(product.price)
    //       return result
    //     }, 0)
    //   }
    // }
  }
</script>

<template>
  <h1>Cart page</h1>

  Number of products in cart:
  {{ $store.state.cart.length }}. Add gift box:
  {{ countUpButton }}
  <input type="button" @click="onClickPlus" value="+" />
  <input
    type="button"
    @click="onClickMinus"
    value="-"
    :disabled="countUpButton < 1"
  />

  <ul>
    <li :key="product.id" v-for="product in $store.state.cart">
      <img alt="" :src="product.image" />
      {{ product.title }}, $ {{ product.price }}, Product id: {{ product.id }}
      <input
        type="button"
        value="Remove from cart"
        @click="$store.commit('removeFromCart', product.id)"
      />
    </li>
  </ul>

  <form>
    <label for="firstName">First name:</label>
    <input id="firstName" name="First name" v-model="firstName" />
    <label for="lastName">Last name:</label>
    <input id="lastName" name="Last Name" v-model="lastName" />
    <label for="email">Email:</label>
    <input id="email" name="Email" v-model="email" />
    <label for="phone">Phone:</label>
    <input :id="phone" name="Phone" v-model="phone" />

    <input
      :disabled="
        phone === '' || firstName === '' || email === '' || lastName === ''
      "
      type="button"
      @click="onSubmit"
      value="Place order!"
    />
    <p v-if="firstName !== ''">Name: {{ firstName }}</p>
    <p v-if="lastName !== ''">Last name: {{ lastName }}</p>
    <p v-if="email !== ''">Email: {{ email }}</p>
    <p v-if="phone !== ''">Phone: {{ phone }}</p>
  </form>

  <footer>
    <p>{{ copy }}</p>
    <p>{{ shopName }}</p>
  </footer>
</template>
