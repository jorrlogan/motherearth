<template>
<div v-bind="updateCartItems">
  <div class="pure-menu pure-menu-horizontal">
  </div>
  <div v-if="cart.length === 0">
      <h2>Your cart is empty</h2>
  </div>
<div v-else>
    <h2>Cart Items</h2>
  <div id="cartTotal">
  <ul id="cartUList">
      <li class="cartList" v-for="item in cart" :key="item"><div>{{item.name}}</div>
      <div><button v-on:click="removeItem(item)">Remove</button></div></li>
  </ul>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: 'Cart',
  
  data() {
      return {
          cart: []
      };
  },
  computed: {
   updateCartItems(){
       this.updateCart();
       return this.cart;
   },

  },
  methods: {
  updateCart(){
        return this.cart = this.$root.$data.cart
    },
    removeItem(item){
        //let spot = this.$root.$data.cart.find(item);
        let spot = 0;
        for(let i = 0; i < this.cart.length; ++i){
            if(this.cart[i].id === item.id){
                spot = i;
                this.$root.$data.cart.splice(spot,1);
            }
        }
    } 
  }
}
</script>







<style scoped>
.cartList{
    width: 100%;
    list-style: none;
    background-color: rgb(248, 161, 110);
    padding: 1%;
    margin: 0.3%

}

h2{
    width: 100%;
    display: block;
    text-align: center;
}

li{
    display: flex;
    justify-content: space-between;
}
</style>
