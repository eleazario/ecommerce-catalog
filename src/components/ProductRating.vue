<template>
    <div class="ratingComponent">
        <div class="ratingNumber">
            {{ rating }}/5
        </div>
        <div class="ratingDotBox">
            <div 
                v-for="(item, index) in 5" :key="index" 
                :class="[Math.round(rating) > index ? 'ratingDotSolid' : '', 'ratingDot']">
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ProductRating',
    props: {
        rating: Number
    }
}
</script>
<style scoped>
.ratingComponent {
    display: flex;
    margin-left: auto;
    gap: 5px;
}

.ratingNumber {
    font-size: 18px;
    color: var(--dark-gray);
}

.ratingDotBox {
    display: flex;
    gap: 2px
}

.ratingDot {
    border-radius: 100%;
    border: 1px solid var(--primary);
    width: 18px;
    height: 18px;
}

.ratingDotSolid {
    background-color: var(--primary);
}
</style>