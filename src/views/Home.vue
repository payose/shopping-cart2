<template>
  <div class="home w-screen">
    <h2 class="py-6 text-center text-5xl font-bold text-green-600">Latest products</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mx-5 md:mx-10 md:p-10">
      <Cards
      v-for="product in products" :key="product.id"
      :product="product"
      class="bg-white shadow-sm rounded-sm">
      </Cards>
    </div>
  </div>
</template>

<script>
import Cards from '@/components/Cards.vue'
import { mapState } from 'vuex'

export default {
  components: {
    Cards
  },

  computed: {
    ...mapState([
      'products'
    ]),
  },
  
}
</script>
