<template>
  <div id="app">
 <navbar></navbar>
<div class = "container">
  <div class="row">
    <div class = "col-sm-9">
   <inventory @newItemAdded="addCartItem" :items="items"></inventory>
  </div>
  <div class = "col-sm-3">
   <cart :items="cart"></cart>
  </div>
</div>
</div>
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import Inventory from './components/Inventory'
import Cart from './components/Cart'
import data from './data.js'

export default {
   components: {
   Inventory,
    Navbar,
    Cart
   },
   data() {
     return {
       items: [],
       cart: [{
         id: 1,
         title: "Test",
         price: 0.0,
         photo: "http://dummyimage.com/286x180.png/5fa2dd/ffffff"
       }]
     }
   },
   mounted() {
     this.items = data
   },
   methods: {
     addCartItem(item) {
       this.cart.push(item)
     }
   }
}
</script>

<style>
.container {
  padding-top: 10px;
}
</style>
