<template>
    <div id="loaderComponent">
        <div class="loader">
            <div></div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'LoaderComponent'
}
</script>
<style scoped>
#loaderComponent {
    background-color: rgb(255, 255, 255, 0.7);
    position: absolute;
    display: flex;
    top: 0;
    width: 100%;
    height: 100%;
    align-items: center;
}

.loader {
    display: flex;
    margin-left: auto;
    margin-right: auto;
    height: 220px;
    width: 220px;
    background-color: var(--white);
    border-radius: 10px;
    box-shadow: 2px 4px 21px 0px #00000033;
}

.loader > div {
    margin: auto;
    width: 120px;
    aspect-ratio: 4;
    --_g: no-repeat radial-gradient(circle closest-side,#000 90%,#0000);
    background: 
        no-repeat radial-gradient(circle closest-side, var(--purple) 90%,#0000) 0%   50%,
        no-repeat radial-gradient(circle closest-side, var(--blue) 90%,#0000) 50%  50%,
        no-repeat radial-gradient(circle closest-side, var(--black) 90%,#0000) 100% 50%;
    background-size: calc(100%/3) 100%;
    animation: l7 0.5s infinite linear;
}

@keyframes l7 {
    33%{background-size:calc(100%/3) 0%  ,calc(100%/3) 100%,calc(100%/3) 100%}
    50%{background-size:calc(100%/3) 100%,calc(100%/3) 0%  ,calc(100%/3) 100%}
    66%{background-size:calc(100%/3) 100%,calc(100%/3) 100%,calc(100%/3) 0%  }
}
</style>