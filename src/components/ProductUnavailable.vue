<template>
    <div id="productUnavailable">
        <div>
            <div class="unvailableDescription">
                This product is unavailable to show
            </div>
            <ProductButton 
                :text="'Next product'"
                :btnStyle="'secondary'"
                @onClickButton="handleNextButtonClick"
                class="nextBtn"
            />
        </div>
    </div>
</template>
<script>
import ProductButton from './ProductButton.vue'

export default {
    name: 'ProductUnavailable',
    components: {
        ProductButton
},
    methods: {
        handleNextButtonClick(){
            this.$emit('onNextButtonClick',)
        }
    }
}
</script>
<style scoped>

#productUnavailable {
    --primary: var(--black);
    position: absolute;
    display: flex;
    top: 0;
    width: 100%;
    height: 100%;
    align-items: center;
}

#productUnavailable > div {
    width: 1034px;
    height: 580px;
    display: flex;
    flex-direction: column;
    margin-left: auto;
    margin-right: auto;
    background-color: var(--white);
    padding: 50px 56px 46px 56px;
    box-shadow: 2px 4px 21px 0px #00000033;
    border-radius: 10px;
    background-image: url('../assets/images/sad-face.png');
    background-repeat: no-repeat;
    background-position: center;
    justify-content: center;
    gap: 13px;
}

.unvailableDescription {
    font-size: 20px;
    font-weight: 400;
    color: var(--black);
    text-align: center;
}

.nextBtn {
    margin: 0 auto;
    padding-left: 169px;
    padding-right: 169px;
}
</style>