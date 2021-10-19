<template>
  <div class="app w-screen">
    <div class="shadow-sm flex justify-between items-center px-5 md:px-10 py-10 w-full h-12 bg-white p-6 mb-12">
      <router-link to="/" class="text-white rounded-md hover:bg-green-600 focus:bg-green-600 focus:outline-none shadow-sm bg-green-500 py-2 px-6">Home</router-link> 
      <router-link to="/cart" class="w-10 relative">
        <img src="./assets/cart.svg" alt="" >
        <span class="item-count">{{ amountOfCartItems }}</span>
      </router-link>
      <!-- <router-link to="/product"></router-link> -->
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  computed: {
    amountOfCartItems(){
      return this.$store.getters.cartItems.reduce((a, b) => a + ( b.quantity ), 0)
    }
  },
   mounted(){
    this.$store.commit('updateCartFromLocalStorage')
    this.items = this.$store.getters.cartItems
  }
}
</script>

<style>
.item-count{
  position: absolute;
    background-color: hsl(355deg 100% 60%);
    color: hsl(0deg 0% 100%);
    font-size: 10px;
    width: 20px;
    height: 20px;
    text-align: center;
    line-height: 22px;
    border-radius: 50%;
    top: -5px;
    right: -10px;
}

</style>
