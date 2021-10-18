<template>
  <div>
    <h1 class="text-green-500 text-3xl mx-5 md:mx-40 md:py-10">My Shopping Cart</h1>
    <div class="bg-white mx-5 my-10 md:mx-40 p-3 md:p-10">
      <CartItemCard 
      v-for="product in products"
      :key="product.id"
      :product="product"
    />

    <CartPaymentCard
    />
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