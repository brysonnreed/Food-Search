<template>
  <div class="bg-white shadow rounded-xl">
    <router-link :to="{ name: `mealDetails`, params: { id: meal.idMeal } }"
      ><img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl h-48 object-cover w-full hover:scale-[1.01] transition-all duration-300"
    /></router-link>

    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        {{ $filters.truncateWords(meal.strInstructions, 20) }}
      </p>
      <div class="flex gap-2 md:gap-5 flex-wrap">
        <DetailsButton :id="meal.idMeal" />
        <YouTubeButton :href="meal.strYoutube" />
      </div>
    </div>
  </div>
</template>

<script setup>
import YouTubeButton from "./YouTubeButton.vue";
import DetailsButton from "./DetailsButton.vue";

const { meal } = defineProps({
  meal: {
    required: true,
    type: Object,
  },
});
</script>

<style lang="scss" scoped></style>
