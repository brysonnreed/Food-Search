<template>
  <section class="text-gray-600 -mt-10 min-h-[90vh]">
    <div class="container mx-auto flex px-5 py-24 items-center justify-center flex-col">
      <img
        class="h-[20vh] mb-10 object-cover object-center rounded"
        alt="Food Search Logo"
        src="/Food-Icon.png"
      />
      <div class="text-center lg:w-2/3 w-full">
        <h1 class="sm:text-6xl text-4xl mb-4 font-bold text-gray-900">
          The Ultimate <span class="text-orange-500">All-in-One</span> Platform for Exploring Every
          Food Craving!
        </h1>
        <p class="mb-8 leading-relaxed">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Ut ipsa, eius est sint fuga ipsum
          quidem, a inventore repellat illo rerum facilis vero debitis expedita doloremque corrupti
          corporis in quae. Lorem ipsum dolor sit amet consectetur adipisicing elit. Ut ipsa, eius
          est sint fuga ipsum quidem.
        </p>
        <div class="flex justify-center">
          <a
            href="/by-name"
            class="inline-flex text-white bg-orange-500 border-0 py-2 px-6 focus:outline-none hover:bg-orange-600 transition-colors duration-300 rounded text-lg"
          >
            Begin Searching
          </a>
          <button
            @click="scrollToRandomMeals"
            class="ml-4 inline-flex text-gray-700 hover:bg-gray-300 border-0 py-2 px-6 focus:outline-none bg-gray-200 rounded text-lg transition-colors duration-300"
          >
            Get Inspiration
          </button>
        </div>
      </div>
    </div>
  </section>
  <div id="random-meals" class="pt-40">
    <h2 class="text-4xl font-bold mb-4 text-center">Discover Random Meals</h2>
    <p class="text-center">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nihil at magni ea aut voluptate
      voluptas! Eligendi quaerat error necessitatibus quis ipsum, recusandae molestias delectus?
      Quaerat cumque distinctio ratione iusto omnis.
    </p>
    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import Meals from "../components/Meals.vue";
import axiosClient from "../axiosClient.js";

const meals = ref([]);

onMounted(async () => {
  for (let i = 0; i < 12; i++) {
    axiosClient.get(`random.php`).then(({ data }) => meals.value.push(data.meals[0]));
  }
});

const scrollToRandomMeals = () => {
  const randomMealsSection = document.getElementById("random-meals");
  if (randomMealsSection) {
    randomMealsSection.scrollIntoView({ behavior: "smooth" });
  }
};
</script>
