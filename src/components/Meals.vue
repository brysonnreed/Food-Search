<template>
  <div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5 py-8">
      <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
    </div>
    <UnknownSearch :meals="meals" :searchPerformed="searchPerformed" />
  </div>
</template>

<script setup>
import MealItem from "./MealItem.vue";
import UnknownSearch from "./UnknownSearch.vue";

const { meals } = defineProps({
  meals: {
    required: true,
    type: Array,
    default: () => [],
  },
  searchPerformed: Boolean,
});
</script>
