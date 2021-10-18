<template>
  <div class="app w-screen">
    <div class="shadow-sm flex justify-between items-center px-5 md:px-10 py-10 w-full h-12 bg-white p-6 mb-12">
      <router-link to="/" class="text-white hover:bg-green-700 focus:bg-green-700 focus:outline-none shadow-sm bg-green-500 rounded-sm py-2 px-6">Home</router-link> 
      <router-link to="/cart" class="text-white hover:bg-green-700 focus:bg-green-700 focus:outline-none shadow-sm bg-green-500 rounded-sm py-2 px-6">Cart</router-link>
      <!-- <router-link to="/product"></router-link> -->
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
   mounted(){
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>

<style>
/* @import "./assets/css/tailwind.css" */

/* #nav a {
  font-weight: bold;
  color:black
}

#nav a.router-link-exact-active {
  color: #fff;
} */
</style>
