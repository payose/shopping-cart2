<template>
  <div class="container text-center pb-4 rounded-lg">
    <div class="p-3">
      <img :src="require(`@/assets/images/${product.image}`)" alt="">
    </div>
    <h3 class="mt-3 font-medium">{{ product.name }}</h3>
    <h5 class="text-gray-500">Price: <span>&#8358;</span> {{ product.price.toFixed(2) }}</h5>
    <div class="flex justify-between items-center mx-4 mt-4"> 
      <button class="flex-1 text-white mr-1 hover:bg-green-600 shadow-sm bg-green-500 rounded-md py-2 px-6" 
        @click="getProduct()">view</button>
      <button class="flex-1 text-white ml-1 hover:bg-green-600 shadow-sm bg-green-500 rounded-md py-2 px-6" 
        @click="addToCart()">Add to cart</button>
    </div>
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
    },
    addToCart() {
      this.$store.commit('addToCart', this.product)
    }
  }
}
</script>

<style scoped>
.cursor:hover{
  cursor: pointer
}
</style>