<template>
  <div id="app">
  
    <router-view :products="products" :cart="cart" @addToCart="addToCart" />
  </div>
</template>

<script>
export default {
  name:'App',
  data() {
    return {
      products: [
        { title: 'sko', price:299 },
        { title: 'socks', price: 99 },
        {title: 'shirt', price:199 },
        { title: 'skate', price: 799 }
      ],
      cart: []
    }
  },
  methods: {
    addToCart(item) {
      this.cart.push(item)
      localStorage.setItem('cart', JSON.stringify(this.cart))
    }
  },
  mounted() {
    let cart = localStorage.getItem('cart');
    if(cart !==null) {
      this.cart = JSON.parse(cart)
    }
  }
}
</script>

<style>

</style>

