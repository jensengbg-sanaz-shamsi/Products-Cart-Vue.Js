<template>
    <article :class="itemClass">
        <p>{{ item.title }}</p>
        <p class="dots"></p>
        <p>{{ item.price }}</p>

    </article>
</template>

<script>
export default {
    name: 'CartItem',
    props: {
        item: Object
    },
    computed: {
        itemClass(){           //switch()
            let className=''
            if(this.item.title === 'sko') {
                className = 'shoe'
            }
            if(this.item.title === 'socks') {
                className = 'socks'
            }
            if(this.item.title === 'shirt') {
                className = 'shirt'
            }
            if(this.item.title === 'skate') {
                className = 'skateboard'
            }

            return className
        }
    }
}
</script>

<style lang="scss" scoped>
article {
    display: flex;

    &.shoe {
        color: red;
    }

    &.socks {
        color: blue;
    }

    &.shirt {
        color: green;
    }

    &.skateboard {
        color: yellow;
    }

    p {
        padding: 0;
        margin: .5rem 0;

        &.dots {
            flex: 1;
            border-bottom: 1px dotted rgba(0,0,0,0.4);
        }
    }
}

</style>