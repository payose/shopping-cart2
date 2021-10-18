<template>
  <div class="container text-center hover:cursor-pointer active:bg-green-700" @click="getProduct()">
    <img :src="require(`@/assets/images/${product.image}`)" alt="">
    <h3 class="mt-3">{{ product.name }}</h3>
    <h5 class="text-green-500">Price: <span>&#8358;</span> {{ product.price.toFixed(2) }}</h5>
    <!-- <p class="text-muted">{{ product.category }}</p> -->
    <!-- <button class="view-product" @click="getProduct()">View</button> -->
  </div>
</template>

<script>
export default {
  props: [
    'product'
  ],
  methods: {
    getProduct () {
      this.$router.push({ path: `/product/${this.product.id}` })
      this.$store.state.product = this.product
      this.$store.dispatch('getProduct')
    }
  }
}
</script>
