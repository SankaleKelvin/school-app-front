<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

import Nav from './components/NavBar.vue';
// import Course from './views/CoursesPage.vue';
// import NewCourse from './views/NewCourse.vue';
</script>

<template>
  <Nav />
  <!-- <Course/> -->
  <!-- <NewCourse/> -->

  <RouterView />
</template>

<style scoped>

</style>
