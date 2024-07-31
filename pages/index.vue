<template>
  <div>
    <Header />
    <RainDropHeader />
    <div class="flex flex-col justify-center items-center">
      <ProjectCard
        v-for="project in projects"
        :key="project.title"
        v-bind="project"
      />
    </div>
  </div>
</template>

<script setup>
const projects = ref([
  {
    title: 'VeggieTable',
    description: 'Resource to help new cooks understand the best way to store their produce.',
    tech: ['Vue', 'Nuxt', 'TypeScript'],
    codeLink: 'https://github.com/patrickjparker/VeggieTable',
    demoLink: 'https://veggie-table.vercel.app/',
    screenshot: '/photos/veggietable.png',
  },
  {
    title: 'Review Analysis Pipeline Tester',
    description: 'As part of a larger project, I needed to test different ways of analyzing customer reviews across a specific type of product. This tool allows me to compare the results of different analysis methods for any type of product.',
    tech: ['PocketBase', 'Redis Queues', 'Nuxt', 'Python', 'Golang'],
    codeLink: 'https://github.com/patrickjparker/pipeline-tester',
    screenshot: '/photos/pipeline.png',
  }
]);
</script>
