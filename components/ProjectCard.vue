<template>
    <div class="flex flex-col sm:flex-row items-center sm:items-stretch m-4 w-4/5 sm:w-2/3 max-w-xl p-4 rounded-lg border border-gray-700 bg-white drop-shadow-md">
        <div class="pr-4">
            <p class="bg-blue-600 w-40 h-40">Placeholder for the image</p>
        </div>
        <div class="flex flex-col justify-between items-center md:items-baseline w-full">
            <div class="flex justify-between items-baseline w-full">
                <p class="font-bold text-lg">{{ props.title }}</p>
                <div class="hidden md:block ml-1">
                    <n-button class="mr-2 mb-1 w-16" tertiary tag="a" :href="props.codeLink">
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
            <div>
                <div class="block md:hidden mt-3">
                    <n-button class="mr-2" tertiary tag="a" :href="props.codeLink">
                        Code
                    </n-button>
                    <n-button type="info" tag="a" v-if="props.demoLink" :href="props.demoLink">
                        Demo
                    </n-button>
                </div>
            </div>
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
    }
});
</script>
