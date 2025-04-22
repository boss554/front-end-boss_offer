<template>
  <header class="bg-white shadow">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Top Row -->
      <div class="flex items-center justify-between py-4">
        <!-- Logo (always visible) -->
        <div class="flex items-center gap-2 flex-shrink-0">
          <!-- Replace with actual logo -->
          <NuxtImg src="" alt="Boss offers logo" class="h-8 w-auto" />
        </div>

        <!-- Search Bar (hidden on mobile) -->
        <div
          class="hidden md:flex flex-1 mx-4 bg-primary-100 rounded-full px-4 py-2"
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

        <!-- Desktop Nav + Auth Buttons -->
        <div class="hidden md:flex items-center gap-6">
          <nav class="flex items-center gap-4">
            <NuxtLink
              to="/"
              class="text-gray-700 font-medium"
              exact-active-class="bg-primary-500 text-white px-4 py-2 rounded-full font-bold"
            >
              Home
            </NuxtLink>
            <NuxtLink
              to="/about-us"
              class="text-gray-700 font-medium"
              exact-active-class="bg-primary-500 text-white px-4 py-2 rounded-full font-bold"
            >
              About
            </NuxtLink>
            <NuxtLink
              class="text-gray-700 font-medium"
              exact-active-class="bg-primary-500 text-white px-4 py-2 rounded-full font-bold"
            >
              Services
            </NuxtLink>
            <NuxtLink
              class="text-gray-700 font-medium"
              exact-active-class="bg-primary-500 text-white px-4 py-2 rounded-full font-bold"
            >
              Contact
            </NuxtLink>
          </nav>

          <!-- Auth Buttons -->
          <div class="flex gap-3">
            <a
              href="sign-in.html"
              class="text-primary-500 border border-primary-300 px-4 py-2 rounded-full"
            >
              Sign in
            </a>
            <a
              href="sign-up.html"
              class="bg-primary-500 text-white px-4 py-2 rounded-full hover:bg-primary-700 transition"
            >
              Sign up
            </a>
          </div>
        </div>

        <!-- Mobile Hamburger -->
        <div class="md:hidden">
          <button @click="toggleMenu" class="text-gray-700">
            <Icon name="mdi-light:menu" class="text-3xl" />
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <div v-if="menuOpen" class="md:hidden pb-4 space-y-3">
        <NuxtLink
          to="/"
          class="block text-gray-700 px-2 py-2 hover:text-blue-600"
          exact-active-class="font-bold text-primary-500"
        >
          Home
        </NuxtLink>
        <NuxtLink
          to="/about-us"
          class="block text-gray-700 px-2 py-2 hover:text-blue-600"
          exact-active-class="font-bold text-primary-500"
        >
          About
        </NuxtLink>
        <NuxtLink
          class="block text-gray-700 px-2 py-2 hover:text-blue-600"
          exact-active-class="font-bold text-primary-500"
        >
          Services
        </NuxtLink>
        <NuxtLink
          class="block text-gray-700 px-2 py-2 hover:text-blue-600"
          exact-active-class="font-bold text-primary-500"
        >
          Contact
        </NuxtLink>
        <div class="flex gap-3 pt-2">
          <a
            href="sign-in.html"
            class="flex-1 text-center text-primary-500 border border-primary-300 px-4 py-2 rounded-full hover:text-white transition"
          >
            Sign in
          </a>
          <a
            href="sign-up.html"
            class="flex-1 text-center bg-primary-500 text-white px-4 py-2 rounded-full hover:bg-primary-700 transition"
          >
            Sign up
          </a>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
const menuOpen = ref(false);
const toggleMenu = () => (menuOpen.value = !menuOpen.value);
</script>
