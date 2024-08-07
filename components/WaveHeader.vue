<template>
    <div class="header" ref="header"></div>
</template>

<script setup>
import Ripple from './Ripple.vue';
import { createApp, ref } from 'vue';

onMounted(() => {
    setMax();
    window.addEventListener('resize', debouncedSetMax);

    header.value.addEventListener('mousemove', mouseoverHandler);

    setRippleLoop();
});

onUnmounted(() => {
    window.removeEventListener('resize', debouncedSetMax);
});

// This is the area where the ripples will be created
const header = ref(null);
let maxHeight = 0;
let maxWidth = 0;
function setMax() {
    maxHeight = header.value.clientHeight;
    maxWidth = header.value.clientWidth;
}

let resizeTimer;
function debouncedSetMax() {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(() => {
        setMax();
    }, 250);
}

let ready = true;
function mouseoverHandler(e) {
    if (ready) {
        ready = false;
        const isHeaderTarget = e.target === header.value;
        if (isHeaderTarget) {
            createRipples(e.offsetX, e.offsetY);
        } else {
            const rect = header.value.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;
            createRipples(x, y);
        }
        setTimeout(() => {
            ready = true;
        }, 200);
    }
}

function setRippleLoop() {
    const ave_interval = 1000;
    const range = 2000;
    function getCoords() {
        const x_buffer = 50;
        const y_buffer = 50;
        return {
            x: Math.random() * (maxWidth - (2 * x_buffer)) + x_buffer,
            y: Math.random() * (maxHeight - (2 * y_buffer)) + y_buffer
        };
    }
    function getSize() {
        return 75 + (Math.random() * 50);
    }

    setInterval(() => {
        const animationState = getComputedStyle(document.body).getPropertyValue('animation-play-state');
        if (animationState === 'paused') {
            return;
        }
        setTimeout(() => {
            const { x, y } = getCoords();
            createRipples(x, y, getSize());
        }, Math.random() * range);
    }, ave_interval);
}

function createRipples(x, y, size) {
    const ripple = document.createElement('div');
    const rippleComp = createApp(Ripple, {
        size: size || 100,
        onDone: () => {
            rippleComp.unmount();
            ripple.remove();
        }
    });
    ripple.style.left = x + 'px';
    ripple.style.top = y + 'px';
    ripple.style.position = 'absolute';
    header.value.appendChild(ripple);
    rippleComp.mount(ripple);
}
</script>

<style scoped>
.header {
    width: 100%;
    height: 100%;
    min-height: 400px;
    max-height: 500px;
    background-color: #117CAA;
    position: relative;
    overflow: hidden;
}
</style>
