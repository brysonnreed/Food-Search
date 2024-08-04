<template>
  <h1 class="text-5xl font-bold mb-4">Search By Name</h1>
  <div class="pb-0">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for Meals"
      @change="searchMeals"
    />
  </div>

  <Meals :meals="meals" :searchPerformed="searchPerformed" />
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { ref, onMounted } from "vue";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);
const searchPerformed = ref(false);

function searchMeals() {
  if (keyword.value) {
    store.dispatch("searchMeals", keyword.value);
    searchPerformed.value = true;
  } else {
    store.commit("setSearchedMeals", []);
    searchPerformed.value = false;
  }
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals(keyword.value);
  }
});
</script>
