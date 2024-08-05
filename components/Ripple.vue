<template>
    <div class="waves">
        <div></div>
        <div></div>
        <div></div>
        <div @animationend="$emit('done')"></div>
    </div>
</template>

<style scoped>

div {
    --duration: 3.7s;
    --delay: 0s;
}

.waves {
    position: absolute;
    width: 200px;
    height: 100px;
    transform: translate(-50%, -50%);
}

.waves > div{
    position: absolute;
    top:0px;
    left: 0px;
    right: 0px;
    bottom: 0px;
    border-radius: 50%;
    opacity: 0;
    border: solid #6497DF 8px;
    animation-name: spread;
    animation-duration: var(--duration);
    animation-delay: var(--delay);
    animation-timing-function: linear;
}

.waves > div:nth-child(2){
    animation-delay: calc(var(--delay) + 0.3s);
}

.waves > div:nth-child(3){
    animation-delay: calc(var(--delay) + 0.6s);
}

.waves > div:nth-child(4){
    animation-delay: calc(var(--delay) + 0.9s);
}

@keyframes spread{
    0% {
        transform: scale(0);
        opacity: 1;
        filter: blur(0px);
    }

    100% {
        transform: scale(1);
        opacity: 0;
        filter: blur(6px);
    }
}
</style>
