<template>
  <div>
    <h1 class="text-green-500 text-3xl mx-5 md:mx-40 md:py-10">My Shopping Cart</h1>
    <div v-if="!products.length" class="p-5 bg-white my-5 mx-5 md:p-10 md:m-20 md:text-center rounded-md shadow-sm">
      <h2 class="text-red-300 md:text-2xl">Opps... Shopping cart empty</h2>
    </div>
    <div v-else>
      <div class="bg-white mx-5 my-10 md:mx-40 p-3 md:p-10 shadow-md rounded-md">
      <CartItemCard 
      v-for="product in products"
      :key="product.id"
      :product="product"
      />
      <CartPaymentCard
      />
      </div>
    </div>
  </div>
</template>

<script>
import CartItemCard from '@/components/CartItemCard.vue'
import CartPaymentCard from '@/components/CartPaymentCard.vue'

export default {
  components: {
    CartItemCard,
    CartPaymentCard
  },
  computed: {
    products() {
      return this.$store.getters.cartItems
    }
  }
}
</script>