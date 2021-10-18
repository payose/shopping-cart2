
<template>
  <div id="app">
    <section>
      <h3 class="text-xl text-green-500">Cart Total: <span>&#8358;</span> {{ cartTotal.toFixed(2) }}</h3>

        <input type="email" v-model="email" required
        placeholder="enter email to checkout"
        class="flex-3 py-2 text-center px-6 md:mr-2">
        <!-- <span v-if="msg">{{msg}}</span> -->
        <hr />
        <div class="container">
          <paystack
            :amount="cartTotal * 100"
            :email="email"
            :paystackkey="PUBLIC_KEY"
            :reference="reference"
            :callback="processPayment"
            :close="close"
            :embed="false"
            class="flex-1 text-white hover:bg-green-700 focus:bg-green-700 focus:outline-none shadow-sm bg-green-500 rounded-sm py-2 px-6"
          >
            <i class="fas fa-money-bill-alt"></i>
            checkout
          </paystack>
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
      // msg: '',
      PUBLIC_KEY: "pk_test_fd6b060ad8fce5062160139d5e1bdbd1630586ea"
    }
  },
  components: {
    paystack
  },
  // watch: {
  //   email(value){
  //     this.email = value;
  //     this.validateEmail(value);
  //   }
  // },
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
    processPayment: () => {
      window.alert("Payment recieved")
    },
    close: () => {
     console.log("You closed checkout page")
    }
  },

  // validateEmail(value){
  //     if (/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(value))
  // {
  //   this.msg = '';
  // } else{
  //   this.msg = 'Invalid Email Address';
  // } 
  // }
  
};
</script>

<style>

input {
  width: 100%;
  padding: 16px 8px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
button {
  padding: 14px 0;
  margin: 10px 0;
  border: none;
  cursor: grabbing;
  width: 100%;
}

</style>
