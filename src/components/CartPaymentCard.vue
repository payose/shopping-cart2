<template>
  <div id="app">
    <section>
      <h3 class="text-xl text-green-500">Cart Total: <span>&#8358;</span> {{ cartTotal.toFixed(2) }}</h3>
      <div class="md:flex items-center bg-gray-10 my-5">
        <input type="email" v-model="email" required
          placeholder="enter email to checkout"
          class="flex-3 py-2 my-2 text-center px-6 sm:mr-2 rounded-md shadow-sm focus:outline-none">
        <div class="container">
          <paystack
            :amount="cartTotal * 100"
            :email="email"
            :paystackkey="PUBLIC_KEY"
            :reference="reference"
            :callback="processPayment"
            :emptyCart="emptyCart"
            :close="close"
            :embed="false"
            class="flex-1 rounded-md text-white hover:bg-green-600 focus:bg-green-700 focus:outline-none shadow-sm bg-green-500 py-2 px-6"
          >
            <i class="fas fa-money-bill-alt"></i>
            checkout
          </paystack>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import paystack from "vue-paystack";
export default {
  name: "App",
  data(){
    return{
      email: '',
      PUBLIC_KEY: "pk_test_fd6b060ad8fce5062160139d5e1bdbd1630586ea"
    }
  },
  components: {
    paystack
  },
  
  computed: {
    cartTotal() {
      return this.$store.getters.cartTotal
      },
    reference() {
      let text = "";
      let possible =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

      for (let i = 0; i < 10; i++)
        text += possible.charAt(Math.floor(Math.random() * possible.length));

      return text;
    }
  },
  
  methods: {
    processPayment()  {
      this.$store.commit('emptyCart')
      window.alert("Payment recieved")
    },
    close: () => {
     console.log("You closed checkout page")
    },
  }
};
</script>

<style scoped>

input {
  width: 100%;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
button {
  border: none;
  cursor: pointer;
  width: 100%;
}

</style>
