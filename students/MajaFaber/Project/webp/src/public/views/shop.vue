<template>
    <div>
        <header>
            <div class="logo">E-shop</div>
            <div class="cart">
                <search />
                <button class="btn-cart" type="button" @click="showCart = !showCart">Корзина</button>
                <cart  v-show="showCart" ref="cartReference" />
            </div>
        </header>
        <main>
            <catalog :filter="search_text"/>
        </main>
    </div>
</template>

<script>
import catalog from '../components/catalog.vue'
import cart from '../components/cart.vue'
import search from '../components/search.vue'
export default {
    data() {
        return {
           // API: 'https://raw.githubusercontent.com/qimitau/js2_12_0502/master/students/MajaFaber/Project/webp/src/public/db/',
            showCart: false,
            search_text: ''
        }
    },
    components: {
        'catalog': catalog,
        'cart': cart,
        'search': search
    },
    methods: {
        getData(url) {
            return fetch(url).then(d => d.json())
        },
        update_search(val = '') {
            this.search_text = val.toLowerCase()
        }
    }
}
</script>

<style>

</style>