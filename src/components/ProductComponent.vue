<template>
    <div id="productComponent"
        :class="[
            product.category === `men's clothing` ? 'menProductComponent' : '',
            product.category === `women's clothing` ? 'womenProductComponent' : '' ,
        ]"
    >
        <div>
            <div class="productImageBox">
                <img :src="product.image" class="productImage" alt="">
            </div>
            <div class="productDetailBox">
                <h2 class="productTitle">{{ product.title }}</h2>
                <div style="display: flex; margin-bottom: 11px;">
                    <h4 class="productCategory">{{ product.category }}</h4>
                    <ProductRating
                        :rating="product.rating.rate"
                    />
                </div>
                <div class="divider"></div>
                <p class="productDescription">{{ product.description }}</p>
                <div class="divider" style="margin-top: auto;"></div>
                <h3 class="productPrice">${{ product.price }}</h3>
                <div class="productButtonBox">
                    <ProductButton 
                        :text="'Buy now'"
                    />
                    <ProductButton 
                        :text="'Next product'"
                        :btnStyle="'secondary'"
                        @onClickButton="handleNextButtonClick"
                    />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import ProductRating from './ProductRating.vue';
import ProductButton from './ProductButton.vue'

export default {
    name: 'ProductCompenent',
    components: {
        ProductRating,
        ProductButton
    },
    props: {
        product: Object
    },
    methods: {
        handleNextButtonClick(){
            this.$emit('onNextButtonClick',)
        }
    }
}
</script>
<style scoped>

.womenProductComponent {
    --primary: var(--purple)
}

.menProductComponent {
    --primary: var(--blue)
}

#productComponent {
    position: absolute;
    display: flex;
    top: 0;
    width: 100%;
    height: 100%;
    align-items: center;
}

#productComponent > div {
    width: 1034px;
    height: 580px;
    display: flex;
    margin-left: auto;
    margin-right: auto;
    background-color: var(--white);
    padding: 50px 56px 46px 56px;
    box-shadow: 2px 4px 21px 0px #00000033;
    gap: 77px;
    border-radius: 10px;
}

.productImageBox {
    display: flex;
    align-items: center;
}

.productImage {
    width: 306px;
}

.productDetailBox {
    display: flex;
    flex-direction: column;
}

.productTitle {
    font-size: 28px;
    color: var(--primary);
    margin-top: 0px;
    margin-bottom: 25px;
}

.productCategory {
    font-size: 18px;
    font-weight: normal;
    color: var(--dark-gray);
    margin: 0
}

.productDescription {
    font-size: 20px;
    color: var(--black);
}

.productPrice {
    font-size: 28px;
    color: var(--primary);
}

.divider{
    border: 1px solid #00000033;
}

.productButtonBox {
    display: flex;
    gap: 19px
}
</style>