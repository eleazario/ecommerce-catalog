<template>
    <button
        @click="handleClickButton"
        :class="[
            btnStyle === 'secondary' ? 'btnSecondary' : 'btnPrimary',
        ]">
        {{ text }}
    </button>
</template>
<script>

export default {
    name: 'ProductButton',
    props: {
        text: {
            type: String,
            required: true
        },
        btnStyle: {
            type: String,
            validator(value){
                return ['primary', 'secondary'].includes(value)
            }
        },
    },
    methods: {
        handleClickButton(){
            this.$emit('onClickButton')
        }
    },
}
</script>
<style scoped>
button {
    border: none;
    border: 3px solid var(--primary);
    border-radius: 4px;
    font-size: 20px;
    font-weight: 600;
    padding: 9px 87px;
    cursor: pointer;
}

.btnPrimary {
    background-color: var(--primary);
    color: var(--white);
}

.btnSecondary {
    background-color: var(--white);
    color: var(--primary);
}
</style>