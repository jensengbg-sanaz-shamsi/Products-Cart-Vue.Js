<template>
    <section id="cart">
        <h2>Cart</h2>
        <CartItem v-for="(item,index) in cart" :key="index" :item="item" />
        <h3>Total cost: {{ totalCost }}</h3>
    </section>
</template>

<script>
import CartItem from '@/components/CartItem.vue'
export default {
    name: 'Cart',
    components: {
        CartItem
    },
    props: {
        cart: Array
    },
    computed: { //method are acting on sth ,if we clicking on smth,but computed is function also but Return something
    //but method doen´t return anything
        totalCost() {
            /*let total = 0;
            this.cart.forEach(item => {
                total += item.price;
            })
            return total*/
            return this.cart.reduce((sum, item) => sum + item.price, 0)
        }
    }
}
</script>

<style>

</style>