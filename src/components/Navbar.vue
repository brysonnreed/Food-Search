<template>
  <header
    class="bg-white shadow h-16 flex justify-between items-stretch sticky top-0 overflow-hidden"
  >
    <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full px-5 font-semibold"
      ><img
        src="/Food-Search.png"
        alt="Food Search Logo"
        class="h-24 hover:scale-105 transition-transform duration-300"
    /></router-link>
    <div class="flex items-center gap-1" id="DesktopNavItems">
      <router-link
        :to="{ name: 'byName' }"
        class="px-2 h-full hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 font-semibold"
      >
        Search Meals
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="px-2 h-full hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 font-semibold"
      >
        Meals By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="px-2 h-full hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 font-semibold"
      >
        Meals by Ingredient
      </router-link>
    </div>
    <button
      aria-label="Open the mobile navigation"
      :class="{ active: isNavOpen, hamburger: true, 'p-2': true }"
      @click="isNavOpen = !isNavOpen"
    >
      <span className="bar"></span>
      <span className="bar"></span>
      <span className="bar"></span>
    </button>
    <div
      class="lg:hidden flex flex-col items-center justify-center lg:space-x-4 overlay gap-5 bg-white"
      :class="{ active: isNavOpen }"
    >
      <router-link :to="{ name: 'home' }" class="items-center px-5 font-semibold"
        ><img
          src="/Food-Search.png"
          alt="Food Search Logo"
          class="h-24 hover:scale-105 transition-transform duration-300"
      /></router-link>
      <div class="flex flex-col items-center justify-evenly gap-1 h-[20vh]">
        <router-link
          :to="{ name: 'byName' }"
          class="px-2 h-full text-2xl hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 text-gray-500"
        >
          Search Meals
        </router-link>
        <router-link
          :to="{ name: 'byLetter' }"
          class="px-2 h-full text-2xl hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 text-gray-500"
        >
          Meals By Letter
        </router-link>
        <router-link
          :to="{ name: 'ingredients' }"
          class="px-2 h-full text-2xl hover:bg-orange-500 hover:text-white inline-flex items-center transition-colors duration-100 text-gray-500"
        >
          Meals by Ingredient
        </router-link>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isNavOpen = ref(false);
</script>
