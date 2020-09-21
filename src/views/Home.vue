<template>
  <main id="home">
    <!--<h1>I´m home!</h1>
    <p>hello i am a {{ local }} and I am {{ localLength}} char long.</p>
    <p>hi,i am an {{ inherited }}</p>
    <p>Hi,I am a {{ compProp}}</p>-->
    <p>{{ joke }}</p>
    <Products :products="products" @addToCart="addToCart"></Products>
    <Cart :cart="cart"></Cart>
  </main>
</template>

<script>
// @ is an alias to /src
import Products from '@/components/Products.vue'
import Cart from '@/components/Cart.vue'

export default {
  name: 'Home',
  components: {
    Products,
    Cart
  },

  props: {
    products:Array,
    cart: Array
  },

  data() {
    return {
      joke: 'getting joke...'
    }
  },

  methods: {
    addToCart(item) {
      this.$emit('addToCart', item)
    }
  },

  /*created() {
    console.log('i´m alive' + Date.now())
  },
  beforeMount() {
    console.log('i´m about to be shown' + Date.now())
  },*/

  async mounted() {
    //console.log('i´m here' + Date.now())
    let resp = await fetch('http://api.icndb.com/jokes/random')
    let data = await resp.json()
    //handle it
    console.log(data)
    this.joke = data.value.joke;

  }
  /*props: { //from parents
    inherited: String
  },
  data() {
    return {
      local: 'local'
    }
  },
  computed: {
    compProp() {
      return ' computed property'
    },
    localLength() {
      return this.local.length
    }
  }*/
}
</script>
<style lang="scss">
#home {
  max-width: 800px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;

  p {
    grid-column: auto/span 2;
  }
}

</style>
