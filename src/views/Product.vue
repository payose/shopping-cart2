<template>
  <div class="flex flex-col md:flex-row items-center mx-5 md:mx-10">
    <img :src="require(`../assets/images/${product.image}`)" alt="" >
    <div class="mt-8  md:ml-10 ">
      <h3 class="text-2xl mb-5 text-gray-600">{{ product.name }}</h3>
      <h3 class="text-xl mb-5 text-gray-600">Category : {{ product.category }}</h3>
      <p class="leading-9 text-gray-600 mb-5">{{product.description }}</p>
      <h3 class="text-xl text-green-600 mb-5"> <span>&#8358;</span> {{ product.price.toFixed(2) }}</h3>

      <div class="flex justify-between items-center"> 
        <button class="flex-1 text-white hoverred-700 mr-2 focus:bg-green-600 focus:outline-none shadow-sm bg-green-500 rounded-sm py-2 px-6" 
        @click="addToCart()">Add to cart</button>
      </div>
    </div>
  </div>
</template>

<script> 
export default {
  data(){
    return{
      product:null
    }
  },
  methods: {
    addToCart() {
      this.$store.commit('addToCart', this.product)
    }
  },

  mounted(){
    this.product = this.$store.state.products[this.$route.params.id-1]
  }
}
</script>