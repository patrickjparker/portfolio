<template>
    <div class="flex p-4 border border-gray-700 bg-white drop-shadow-md m-4">
        <div class="pr-4">
            <p class="bg-blue-600 w-32 h-32">Placeholder for the image</p>
        </div>
        <div>
            <p>{{ props.title }}</p>
            <p>{{ props.description }}</p>
            <p>Tech used: 
                <span v-for="tech, i in props.tech" :key="i">
                    {{ tech }}{{ props.tech.length - 1 !== i ? ', ' : ''}}
                </span>
            </p>
            <a :href="props.codeLink">Code</a>
            <a v-if="props.demoLink" :href="props.demoLink">Demo</a>
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
