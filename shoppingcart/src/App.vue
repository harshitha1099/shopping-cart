<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">View products</button>
      {{cart.length}} in cart
      <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";

export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: []
    };
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product), 1);
    },
    navigateTo(page) {
      this.page = page;
    }
  },
  components: { Products, Cart }
};
</script>

<style>
body {
  margin: 0;
}

.products {
      display: flex;
  grid-template-columns: 1fr 1fr;
  padding: 10px;
    justify-content: space-evenly;
}

.products button {
  padding: 10px;
  background-color: rgba(253, 33, 52, 0.733);
  color: white;
  outline: none;
  border: navy;
  cursor: pointer;
  text-align: left;
}
</style>

<style scoped>
header {
  height: 60px;
  box-shadow: 2px 2px 5px rgb(231, 98, 46);
  background-color: rgb(160, 247, 109);
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}

header button {
  padding: 10px;
  border: none;
  cursor: pointer;
  color: white;
  background-color: rgb(170, 90, 84);
}
</style>