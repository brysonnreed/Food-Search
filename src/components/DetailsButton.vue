<template>
  <router-link
    :to="{ name: `mealDetails`, params: { id: id } }"
    class="px-3 py-2 rounded text-white bg-orange-500 hover:bg-orange-600 border-2 border-orange-500 hover:border-orange-600 transition-colors duration-200"
    ><slot>View Details</slot></router-link
  >
</template>

<script setup>
const props = defineProps({
  id: String,
});
</script>
