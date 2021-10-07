<template>
  <div>
    <h1>Products</h1>
    <div class="products">
      <div v-for="(product, index) in products" :key="index">
        <h3>{{ product.name }}</h3>
        <div class="cost">&#8377;{{ product.cost }}</div>
        <img :src="product.image" class="image"/>
        <button v-on:click="addItemToCart(product)">Add to cart</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      products: [
        {
          name: "Watch",
          cost: "25000",
          image:
            "https://lh3.googleusercontent.com/yV4ThMygj-bejcFZBem6Q7_GdAN1ziUdbF-2aRpecEqT-btYlkrbI5JAILMS8_uGNpHyRA=s162",
        },
        {
          name: "Pizza",
          cost: "299",
          image:
           "https://lh3.googleusercontent.com/60Yu_XihVFOy7ctuJpHfer6aHAH7IDpHpBjXuyXSymdv5r8n3hrXI9kP5Z0iaBo5KTWw=s158",
        },
      ],
    };
  },
  methods: {
    addItemToCart(product) {
      this.$emit("addItemToCart", product);
    },
  },
};
</script>

<style>
.image{
  width: 300px;
}
</style>