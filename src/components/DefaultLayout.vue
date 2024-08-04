<template>
  <div class="bg-gray-100 min-h-screen">
    <navbar />
    <main class="max-w-6xl mx-auto md:px-5 px-2 py-20"><router-view /></main>
  </div>
</template>

<script setup>
import Navbar from "./Navbar.vue";
</script>
