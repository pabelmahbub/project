<script setup>
import SingleProject from '../components/SingleProject.vue'
import { ref } from 'vue'
const projects = ref(null)


fetch('http://localhost:3000/projects')
    .then(response => response.json())
    .then(data => projects.value = data);



const handleDelete=(id)=>{
   this.projects = this.projects.filter((project)=>{
    return project.id !== id
   })
}


</script>

<template>
    <div class="home">
        <div v-if="projects.length">
         <div v-for="project in projects" :key="project.id" ><p><SingleProject :project="project" @delete="handleDelete"/></p></div>
        </div>
    </div>
</template>



<style lang="scss" scoped>

</style>