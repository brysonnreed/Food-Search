<template>
  <h1 class="text-5xl font-bold mb-4">Meals with {{ ingredient.strIngredient }}</h1>
  <Meals :meals="meals" :searchPerformed="searchPerformed" />
</template>

<script setup>
import { onMounted, ref } from "vue";
import { computed } from "@vue/reactivity";
import store from "../store";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";

const route = useRoute();
const meals = computed(() => store.state.mealsByIngredient);
const searchPerformed = ref(false);

const ingredient = computed(() => store.state.ingredient);

onMounted(() => {
  store.dispatch("searchMealsByIngredient", route.params.ingredient);
  searchPerformed.value = true;
});
</script>
