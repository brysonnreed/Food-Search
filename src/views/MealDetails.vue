<template>
  <div class="">
    <div class="pb-10">
      <h1 class="text-5xl font-bold mb-5">{{ meal.strMeal }}</h1>
      <div class="flex gap-5 flex-wrap">
        <p class="bg-orange-500 text-white rounded-md shadow inline-flex px-3 py-2">
          {{ meal.strCategory }}
        </p>

        <p class="bg-gray-300 rounded-md shadow inline-flex px-3 py-2">
          {{ meal.strArea }}
        </p>
      </div>
    </div>
    <img
      :src="meal.strMealThumb"
      :alt="meal.strMeal"
      class="w-full object-cover md:h-[70vh] rounded-xl shadow-md"
    />
    <p class="pt-2 text-gray-400">Tags: {{ meal.strTags }}</p>
    <div class="py-10">
      <h2 class="text-3xl font-bold pb-2">Instructions:</h2>
      <p>{{ meal.strInstructions }}</p>
    </div>
    <div class="grid sm:grid-cols-2 grid-cols-1">
      <div class="py-10">
        <h2 class="text-3xl font-bold pb-2">Ingredients:</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)"
            ><li v-if="meal[`strIngredient${ind + 1}`]">
              {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}
            </li></template
          >
          {{
            meal.strIngredients
          }}
        </ul>
      </div>

      <div class="py-10">
        <h2 class="text-3xl font-bold pb-2">Measures:</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)"
            ><li v-if="meal[`strMeasure${ind + 1}`]">
              {{ ind + 1 }}. {{ meal[`strMeasure${ind + 1}`] }}
            </li></template
          >
          {{
            meal.strIngredients
          }}
        </ul>
      </div>
    </div>

    <div class="flex gap-5 flex-wrap">
      <a
        :href="meal.strSource"
        target="_blank"
        class="px-3 py-2 rounded text-white bg-orange-500 hover:bg-orange-600 border-2 border-orange-500 hover:border-orange-600 transition-colors duration-200"
      >
        More Info
      </a>
      <YouTubeButton :href="meal.strYoutube" />
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axiosClient from "../axiosClient";
import YouTubeButton from "../components/YouTubeButton.vue";

const route = useRoute();
const meal = ref({});

onMounted(() => {
  //   route.params.id;
  axiosClient.get(`lookup.php?i=${route.params.id}`).then(({ data }) => {
    meal.value = data.meals[0] || {};
  });
});
</script>
