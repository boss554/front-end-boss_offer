<template>
  <header class="bg-white shadow">
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between py-4">
        <div class="flex items-center gap-2 flex-shrink-0">
          <NuxtImg src="" alt="Boss Offers Logo" class="h-8 w-auto" />
        </div>

        <div class="flex gap-2">
          <div
            class="hidden md:flex flex-1 mx-6 bg-primary-100 rounded-full pl-4 pr-2 py-2"
          >
            <input
              type="text"
              placeholder="Search here..."
              class="flex-1 bg-transparent outline-none text-sm"
            />
            <button
              class="bg-primary-500 text-white px-4 py-2 rounded-full text-sm"
            >
              Search
            </button>
          </div>

          <div class="hidden md:flex items-center gap-3">
            <NuxtLink
              to="/sign-in"
              class="text-primary-500 border border-primary-300 px-4 py-2 rounded-full hover:bg-primary-500 hover:text-white transition"
            >
              Sign in
            </NuxtLink>
            <NuxtLink
              to="/sign-up"
              class="bg-primary-500 text-white px-4 py-2 rounded-full hover:bg-primary-700 transition"
            >
              Sign up
            </NuxtLink>
          </div>
        </div>

        <div class="md:hidden">
          <button @click="toggleMenu" class="text-gray-700">
            <Icon name="mdi-light:menu" class="text-3xl" />
          </button>
        </div>
      </div>

      <nav
        class="hidden md:flex items-center justify-center gap-8 py-2 border-t border-gray-200"
      >
        <NuxtLink
          to="/"
          class="text-gray-700 font-medium hover:text-primary-500 transition"
          exact-active-class="font-bold text-primary-500"
        >
          Home
        </NuxtLink>
        <NuxtLink
          to="/about-us"
          class="text-gray-700 font-medium hover:text-primary-500 transition"
          exact-active-class="font-bold text-primary-500"
        >
          About
        </NuxtLink>
        <NuxtLink
          to="/services"
          class="text-gray-700 font-medium hover:text-primary-500 transition"
          exact-active-class="font-bold text-primary-500"
        >
          Services
        </NuxtLink>
        <NuxtLink
          to="/contact"
          class="text-gray-700 font-medium hover:text-primary-500 transition"
          exact-active-class="font-bold text-primary-500"
        >
          Contact
        </NuxtLink>
      </nav>

      <div
        v-if="menuOpen"
        class="md:hidden flex flex-col gap-3 pb-4 mt-2 border-t border-gray-200"
      >
        <NuxtLink
          to="/"
          class="block text-gray-700 px-2 py-2 hover:text-primary-500"
          exact-active-class="font-bold text-primary-500"
        >
          Home
        </NuxtLink>
        <NuxtLink
          to="/about-us"
          class="block text-gray-700 px-2 py-2 hover:text-primary-500"
          exact-active-class="font-bold text-primary-500"
        >
          About
        </NuxtLink>
        <NuxtLink
          to="/services"
          class="block text-gray-700 px-2 py-2 hover:text-primary-500"
          exact-active-class="font-bold text-primary-500"
        >
          Services
        </NuxtLink>
        <NuxtLink
          to="/contact"
          class="block text-gray-700 px-2 py-2 hover:text-primary-500"
          exact-active-class="font-bold text-primary-500"
        >
          Contact
        </NuxtLink>

        <div class="flex gap-3 pt-2">
          <NuxtLink
            to="/sign-in"
            class="flex-1 text-center text-primary-500 border border-primary-300 px-4 py-2 rounded-full hover:bg-primary-500 hover:text-white transition"
          >
            Sign in
          </NuxtLink>
          <NuxtLink
            to="/sign-up"
            class="flex-1 text-center bg-primary-500 text-white px-4 py-2 rounded-full hover:bg-primary-700 transition"
          >
            Sign up
          </NuxtLink>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from "vue";

const menuOpen = ref(false);
const toggleMenu = () => (menuOpen.value = !menuOpen.value);
</script>
