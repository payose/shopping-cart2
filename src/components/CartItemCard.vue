<template>
  <div class="flex items-center bg-blue-50 border-solid border-4 border-blue-50 rounded-md shadow-md my-5">
    <div class="bg-white flex justify-center rounded-md m-1">
      <img :src="require(`../assets/images/${product.image}`)" class="m-5 items-center transform motion-safe:hover:scale-110 max-h-16 md:max-h-28" alt="">
    </div>
    <div class="text-gray-500 ml-2 md:ml-10 flex flex-col md:flex-row flex-3 justify-between content-center w-4/5">
      <div class="flex flex-wrap content-center">
        <p class="text-sm md:text-xl inline">{{ product.name}}</p>
      </div>
        <div class="flex items-center"> 
          <button class="px-3 py-1 md:py-3 md:px-5 rounded-md border-solid border-2 border-blue-50 bg-white" @click="addToCart()">+</button>
          <button class="px-3 py-1 md:py-3 md:px-5 rounded-md border-solid border-2 border-blue-50 bg-white">{{product.quantity }}</button>
          <button class="px-3 py-1 md:py-3 md:px-5 rounded-md border-solid border-2 border-blue-50 bg-white" @click="removeFromCart()">-</button>
        </div>
        <div class="flex flex-wrap content-center mr-3">
        <p class="text-sm text-green-500"> Total Cost: <span>&#8358;</span> {{ itemCost.toFixed() }}</p>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  props: [
    'product'
  ],

  computed: {
    itemCost(){
      return this.product.price * this.product.quantity
    }
  },
  methods: {
    addToCart() {
      this.$store.commit('addToCart', this.product)
    },

    removeFromCart() {
      this.$store.commit('removeFromCart', this.product)
    }
  }
}
</script>