<script>
  import TheLogoPage from './components/TheLogoPage.vue'

  export default {
    components: {
      TheLogoPage
    }
  }
</script>

<template>
  <nav>
    <div>
      <!-- <TheLogoPage shop="The online Bazar" /> -->

      <ul id="listContainer">
        <li>
          <RouterLink to="/">
            <TheLogoPage shop="The online Bazar"
          /></RouterLink>
        </li>
        <li>
          <RouterLink to="/">Home</RouterLink>
        </li>
        <li>
          <RouterLink to="/shop">Shop</RouterLink>
        </li>
        <li>
          <RouterLink to="/newsLetter">News Letter</RouterLink>
        </li>
        <li>
          <RouterLink to="/cart">Cart</RouterLink>
        </li>
      </ul>
    </div>
  </nav>

  <main><RouterView /></main>
</template>

<style lang="scss">
  $darkg: #2a2e32;
  $lightg: #f8f9fa;

  nav {
    background-color: $darkg;
    color: $lightg;
  }
  nav ul li a {
    color: $lightg;
    text-decoration: none;
  }
  #listContainer {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-left: 0.5rem;
    margin-right: 29rem;
    // padding-bottom: 0.5rem;
    padding-top: 1rem;
    padding-bottom: 1rem;
  }
</style>
