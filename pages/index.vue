<template>
  <div>
    <p>Hello to all</p>
    <div class="flex flex-col justify-center items-center">
      <ProjectCard
        v-for="project in projects"
        :key="project.title"
        :title="project.title"
        :description="project.description"
        :tech="project.tech"
        :codeLink="project.codeLink"
        :demoLink="project.demoLink"
      />
    </div>
  </div>
</template>

<script setup>
const projects = ref([
  {
    title: 'First Project',
    description: 'This is the sd',
    tech: ['werw', 'TypeScript'],
    codeLink: 'sdfsdfsdf'
  },
  {
    title: 'Second Project',
    description: 'This is the sd',
    tech: ['werw', 'TypeScript'],
    codeLink: 'sdfsdfsdf',
    demoLink: 'sdfsdfsdf'
  }
]);
</script>
