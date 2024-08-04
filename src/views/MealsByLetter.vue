<template>
  <div class="flex justify-center gap-2 mt-2 flex-wrap">
    <router-link
      :to="{ name: 'byLetter', params: { letter } }"
      v-for="letter of letters"
      :key="letter"
    >
      {{ letter }}
    </router-link>
  </div>
  <Meals :meals="meals" :searchPerformed="searchPerformed" />
</template>

<script setup>
import { useRoute } from "vue-router";
import store from "../store";
import { computed } from "@vue/reactivity";
import { onMounted, ref, watch } from "vue";
import Meals from "../components/Meals.vue";

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(() => store.state.mealsByLetter);
const searchPerformed = ref(false);

watch(route, () => {
  store.dispatch("searchMealsByLetter", route.params.letter);
  searchPerformed.value = true;
});

onMounted(() => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});
</script>
