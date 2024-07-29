<template>
    <div class="flex flex-col sm:flex-row items-center sm:items-stretch m-4 p-4 w-4/5 sm:w-2/3 max-w-2xl rounded-lg border border-gray-700 bg-white drop-shadow-md min-h-52">
        <div class="pr-4 flex items-center w-80">
            <img :src="props.screenshot" class="w-full h-auto" alt="Screenshot of Project">
        </div>
        <div class="flex flex-col justify-between items-center md:items-baseline w-full">
            <div class="flex flex-col md:flex-row justify-between items-baseline w-full">
                <p class="font-bold text-lg mr-1 mb-1">{{ props.title }}</p>
                <div>
                    <n-button class="mr-1 mb-1 w-16" tertiary tag="a" :href="props.codeLink">
                        Code
                    </n-button>
                    <n-button
                        class="w-16"
                        type="info"
                        tag="a"
                        v-if="props.demoLink"
                        :href="props.demoLink"
                    >
                        Demo
                    </n-button>
                </div>
            </div>
            <p class="mb-1">{{ props.description }}</p>
            <p>Tech used: 
                <n-tag class="mr-1" v-for="tech, i in props.tech" :key="i">
                    {{ tech }}
                </n-tag>
            </p>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    title: {
        type: String,
        required: true
    },
    description: {
        type: String,
        required: true
    },
    tech: {
        type: Array,
        required: true
    },
    codeLink: {
        type: String,
        required: true
    },
    demoLink: {
        type: String,
        required: false
    },
    screenshot: {
        type: String,
        required: true
    }
});
</script>
