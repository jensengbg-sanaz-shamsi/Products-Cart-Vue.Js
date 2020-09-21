<template>
    <section id="products">
        <h2>Products</h2>
        <article v-for="(item, index) in products" :key="index" @click="addToCart(item)">
            <p>{{ item.title }}</p>
            <p>{{ item.price }}</p>
        </article>
    </section>
</template>

<script>
export default {
    name: 'Products',
    props: {
        products: Array
    },
    methods: {
        addToCart(item) {
            this.$emit('addToCart', item)
        }
    }
}
</script>

<style lang="scss">
#products {
    article {
        display: flex;
        justify-content: space-between;
        padding: 1rem;

        &:hover {
            cursor: pointer;
            background: grey;
        }
    }
}

</style>