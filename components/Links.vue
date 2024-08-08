<template>
    <div class="flex">
        <Github :class="iconClass" @click="openPage(GitHubUrl)" />
        <Linkedin :class="iconClass" @click="openPage(LinkedInUrl)" />
        <FileAltRegular :class="iconClass" @click="openPage(ResumeUrl, true)" />
    </div>
</template>

<script setup>
import { Github, Linkedin, FileAltRegular } from '@vicons/fa';

const iconClass = 'w-6 h-6 text-white ml-2 cursor-pointer';

const ResumeUrl = "/files/PublicResume.pdf";
const GitHubUrl = "https://github.com/patrickjparker";
const LinkedInUrl = "https://www.linkedin.com/in/patrick-j-parker-";

function openPage(url, newTab = false) {
    if (newTab) {
        window.open(url, '_blank');
    } else {
        window.location.href = url;
    }
}
</script>
