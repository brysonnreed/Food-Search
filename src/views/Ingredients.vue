<template>
  <div>
    <h1 class="text-5xl font-bold mb-4">Search By Ingredients</h1>
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full mb-10"
      placeholder="Search for Ingredients"
      @change="searchMeals"
    />
    <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
      <!-- <router-link
        :to="{ name: 'byIngredient', params: { ingredient: ingredient.strIngredient } }"
        v-for="ingredient in computedIngredients"
        :key="ingredient.idIngredient"
        class="bg-white rounded p-3 mb-3 shadow block hover:scale-[1.015] transition-transform duration-300"
      >
        <h2 class="text-2xl font-bold">{{ ingredient.strIngredient }}</h2>
      </router-link> -->
      <a
        href="#"
        @click.prevent="openIngredient(ingredient)"
        v-for="ingredient in computedIngredients"
        :key="ingredient.idIngredient"
        class="bg-white rounded p-3 mb-3 shadow block hover:scale-[1.015] transition-transform duration-300"
      >
        <h2 class="text-2xl font-bold">{{ ingredient.strIngredient }}</h2></a
      >
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import axiosClient from "../axiosClient";
import { useRouter } from "vue-router";
import store from "../store";

const router = useRouter();
const keyword = ref("");
const ingredients = ref([]);

const computedIngredients = computed(() => {
  if (!computedIngredients) return ingredients;

  return ingredients.value.filter((i) =>
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  );
});

function openIngredient(ingredient) {
  store.commit("setIngredient", ingredient);
  router.push({
    name: "byIngredient",
    params: { ingredient: ingredient.strIngredient },
  });
}

onMounted(() => {
  axiosClient.get("list.php?i=list").then(({ data }) => {
    ingredients.value = data.meals;
  });
});
</script>
