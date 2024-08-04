<template>
  <div
    v-if="searchPerformed && !meals.length && shouldShow == true"
    class="flex flex-col justify-center items-center text-gray-600 min-h-[60vh]"
  >
    <h2 class="text-[100px] text-orange-500 font-bold text-center">Oops</h2>
    <p class="text-2xl text-gray-500 mb-10 text-center">
      We couldn't find any meals with that Search.
    </p>
    <router-link
      to="/"
      class="px-3 py-2 rounded text-white bg-orange-500 hover:bg-orange-600 border-2 border-orange-500 hover:border-orange-600 transition-colors duration-200"
      >Go back home</router-link
    >
    <img src="/Cartoon-fast-food.png" alt="Food Illustration" />
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

const { meals } = defineProps({
  meals: Object,
  searchPerformed: Boolean,
});

const shouldShow = ref(false);

onMounted(() => {
  setTimeout(() => {
    shouldShow.value = true;
  }, 1000);
});
</script>
