<template>
    <div>
        <div class="header" ref="header">
        </div>
        <n-button @click="createRipples(100, 100)">Click me</n-button>
    </div>
</template>

<script setup>
import Ripple from './Ripple.vue';
import { createApp, ref } from 'vue';

// This is the area where the ripples will be created
const header = ref(null);
let maxHeight = 0;
let maxWidth = 0;

onMounted(() => {
    maxHeight = header.value.clientHeight;
    maxWidth = header.value.clientWidth;

    setInterval(() => {
        setTimeout(() => {
            createRipples(Math.random() * maxWidth, Math.random() * maxHeight);
        }, Math.random() * 1000);
    }, 500);
});

function createRipples(x, y) {
    const ripple = document.createElement('div');
    const rippleComp = createApp(Ripple, {
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
