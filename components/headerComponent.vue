<template>
    <header class="header-section">
      <!-- top header start -->
      <div class="container mx-auto px-4">
          <div class="py-4 md:py-6 mt-0 lg:mt-6">
              <div class="flex flex-wrap items-center">
                  <div class="lg:w-1/4 2xl:w-1/6">
                      <a href="index.html" class="hidden lg:flex items-center gap-2">
                          <!-- <img src="assets/images/logo.png" alt="logo" class="h-auto"> -->
                      </a>
                  </div>
                  <div class="lg:w-3/4 2xl:w-5/6 flex items-center gap-3 md:gap-4">
                      <div class="w-full bg-gray-100 rounded-full p-2 transition border hidden sm:block">
                          <form action="#" class="flex items-center justify-between">
                              <input type="text" placeholder="Search here..." class="px-3 md:px-4 w-full bg-transparent outline-none">
                              <button class="bg-gray-300 p-2 rounded-full flex items-center justify-center">
                                  <i class="ph ph-magnifying-glass text-gray-700"></i>
                              </button>
                          </form>
                      </div>
                      <span class="hidden sm:flex items-center relative border-l h-6 mx-3"></span>
                      <div class="flex gap-4">
                          <a href="sign-in.html" class="flex items-center gap-2 md:gap-3 rounded-full py-2 md:py-3 px-5 md:px-7 border border-gray-300 hover:bg-gray-200 transition">
                              <span class="text-sm whitespace-nowrap">Sign in</span>
                              <i class="ph ph-arrow-right"></i>
                          </a>
                          <a href="sign-up.html" class="flex items-center gap-2 md:gap-3 rounded-full py-2 md:py-3 px-5 md:px-7 bg-gray-300 hover:bg-gray-400 transition">
                              <span class="text-sm whitespace-nowrap">Sign up</span>
                              <i class="ph ph-arrow-right"></i>
                          </a>
                      </div>
                  </div>
              </div>
          </div>
      </div>

      <!-- top header end -->
  
      <!-- main header start -->
      <div class="main-navbar py-3 lg:py-5 mx-0 md:mx-3 bg-gray-100">
        <div class="container mx-auto px-4">
            <nav class="w-full">
                <div class="flex items-center justify-between">
                    <a href="index.html" class="block lg:hidden">
                        <!-- <img class="hidden md:block" src="assets/images/logo.png" alt="logo"> -->
                        <!-- <img class="block md:hidden" src="assets/images/fav.png" alt="logo"> -->
                    </a>
                    <div class="flex gap-6">
                        <div class="switch-wrapper-top flex"></div>
                        <button class="navbar-toggle-btn block" type="button">
                            <span><NuxtLink to="/"> Home </NuxtLink></span>
                            <span><NuxtLink to="/about-us"> About-us</NuxtLink></span>

                            <span></span>
                            <span></span>
                            <span></span>
                        </button>
                    </div>
                </div>

                <div class="navbar-toggle-item">
                    <div class="flex flex-col lg:flex-row gap-5 items-start lg:items-center justify-between mt-5 lg:mt-0">
                        <a href="index.html" class="navbar-brand logo">
                            <!-- <img class="w-full" src="assets/images/fav.png" alt="logo"> -->
                        </a>

                        <div class="right-area hidden lg:flex gap-4 items-center">
                          <span class="v-line flex items-center justify-center"></span>
                            <button class="flex items-center justify-center" data-bs-toggle="modal" data-bs-target="#submitCoupon">
                                <span class="flex items-center justify-center text-lg">
                                    <i class="ph ph-tag"></i>
                                </span>
                            </button>
                            <span class="v-line flex items-center justify-center"></span>
                            <a href="stores-style-6.html" class="flex items-center justify-center">
                                <span class="flex items-center justify-center text-lg">
                                    <i class="ph ph-heart-straight"></i>
                                </span>
                            </a>
                            <span class="v-line flex items-center justify-center"></span>
                        </div>
                    </div>
                </div>
            </nav>
        </div>
      </div>

      <!-- main header end -->
    </header>
  </template>
  
  <script setup>
  defineOptions({
    name: 'NavbarComponent',
  });
  </script>
  
  <style scoped>
  /* Add your custom styles here */
  </style>