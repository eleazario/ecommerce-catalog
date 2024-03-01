<template>
    <div id="app">
        <div
            :class="[ 
                'topBackground',
                product.category === `men's clothing` ? 'menBackground' : '',
                product.category === `women's clothing` ? 'womenBackground' : '',
                product.category !== `women's clothing` && product.category !== `men's clothing` ? 'unavailableBackground' : ''
            ]">
        </div>
        <div class="bottomBackground"></div>
        <ProductComponent 
            v-if="product.category === `men's clothing` || product.category === `women's clothing`"
            :product="product"
            @onNextButtonClick="nextProduct"
        />
        <ProductUnavailable 
            v-else
            @onNextButtonClick="nextProduct"
        />
        <LoaderComponent v-if="loading === true" />
    </div>
</template>

<script>
import ProductComponent from './components/ProductComponent.vue';
import ProductUnavailable from './components/ProductUnavailable.vue';
import LoaderComponent from './components/LoaderComponent.vue';

export default {
    name: 'App',
    components: {
        ProductComponent,
        ProductUnavailable,
        LoaderComponent
},

    data(){
        return {
            product: {},
            loading: false
        }
    },

    methods: {
        getProduct(index){
            try {
                this.loading = true
                fetch(`https://fakestoreapi.com/products/${index}`)
                    .then(res=>res.json())
                    .then(json=>this.product=json)
                    .then(()=>this.loading = false)
            } catch (error) {
                console.log(error);
            }
        },
        nextProduct(){
            if (this.product.id===20)
                this.getProduct(1)
            else
                this.getProduct(++this.product.id)
        }
    },

    beforeMount(){
        this.getProduct(1)
    }
}
</script>

<style>
html, body, #app {
    margin: 0;
    height: 100%
}

#app {
    font-family: "Inter", sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    position: relative;
}

.topBackground {
    background-image: url(./assets/images/bg-pattern.svg);
    height: 65%;
}

.menBackground {
    background-color: var(--light-blue);
}

.womenBackground {
    background-color: var(--light-purple);
}

.unavailableBackground {
    background-color: var(--light-gray);
    background-image: none;
}

.bottomBackground {
    background-color: var(--white);
    height: 35%;
}

</style>
