<template>
    <div class="container">
        <div v-for="_, index in Array(9)" :key="index" class="rain">
            <div class="waves">
                <div></div>
                <div></div>
                <div></div>
                <div></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container{
    width: 100%;
    height: 100%;
    min-width: 600px;
    max-width: 800px;
    min-height: 400px;
    max-height: 500px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    background-color: #117CAA;
    overflow: hidden;
}

.rain{
    position: relative;
    width: 100%;
    height: 100%;
}

.rain:nth-of-type(1){
    --duration: 3.7s;
    --delay: 1s;
    transform: translate(10%, 10%) scale(0.9);
}

.rain:nth-of-type(2){
    --duration: 3.1s;
    --delay: 1.2s;
    transform: translate(-20%, 40%) scale(1.3);
}

.rain:nth-of-type(3){
    --duration: 3.3s;
    --delay: 2s;
    transform: translate(0%, 50%) scale(1.1);
}

.rain:nth-of-type(4){
    --duration: 3s;
    --delay: 4s;
    transform: translate(0%, -10%) scale(1.2);
}

.rain:nth-of-type(5){
    --duration: 3.5s;
    --delay: 0s;
    transform: translate(10%, 0%) scale(0.9);
}

.rain:nth-of-type(6){
    --duration: 3s;
    --delay: 2.7s;
    transform: translate(-20%, 0%) scale(1);
}

.rain:nth-of-type(7){
    --duration: 2.8s;
    --delay: 1.3s;
    transform: translate(20%, -40%) scale(1.2);
}

.rain:nth-of-type(8){
    --duration: 3.2s;
    --delay: 0s;
    transform: translate(20%, 0%) scale(1);
}

.rain:nth-of-type(9){
    --duration: 3s;
    --delay: 0.5s;
    transform: translate(0%, -10%) scale(1.3);
}

    .waves > div{
        position: absolute;
        top:0px;
        left: 0px;
        right: 0px;
        bottom: 0px;
        border-radius: 50%;
        border: solid #6497DF 8px;
        animation-name: spread;
        animation-duration: var(--duration);
        animation-delay: var(--delay);
        animation-iteration-count: infinite;
        animation-timing-function: linear;
        animation-fill-mode: backwards;
    }

    .waves > div:nth-child(2){
        animation-delay: calc(var(--delay) + 0.3s);
    }

    .waves > div:nth-child(3){
        animation-delay: calc(var(--delay) + 0.6s);
    }

    .waves > div:nth-child(4){
        animation-delay: calc(var(--delay) + 0.6s);
    }

    @keyframes spread{
        0%{
            transform: scale(0);
            opacity: 1;
            filter: blur(0px);
        }
        40%{
            transform: scale(0);
            opacity: 1;
            filter: blur(0px);
        }

        100%{
            transform: scale(1);
            opacity: 0;
            filter: blur(6px);
        }
    }

</style>
