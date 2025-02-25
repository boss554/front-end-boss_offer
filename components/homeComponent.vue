<template>
    
    <section class="bg-gray-100 py-12 md:py-20">
      <div class="container mx-auto px-4">
        <!-- Header Section with Filter Options -->
        <div class="flex flex-col md:flex-row justify-between items-center pb-6 md:pb-10">
          <h3 class="text-xl font-semibold text-gray-800">Popular Offers</h3>
          <ul class="flex flex-wrap gap-4 bg-white p-2 rounded-full shadow">
            <li v-for="(filter, index) in filters" :key="index" @click="activeFilter = filter.value"
                :class="{'bg-blue-500 text-white': activeFilter === filter.value, 'text-gray-700': activeFilter !== filter.value}"
                class="cursor-pointer px-4 py-2 rounded-full transition">
              {{ filter.label }}
            </li>
          </ul>
        </div>
  
        <!-- Coupon Deal Cards -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
          <div v-for="(offer, index) in filteredOffers" :key="index" class="bg-white p-5 rounded-lg shadow-lg flex flex-col items-center">
            <img :src="offer.image" :alt="offer.title" class="w-20 h-20 object-contain" />
            <p class="text-lg font-medium text-gray-800 mt-4">{{ offer.title }}</p>
            <button class="mt-3 px-5 py-2 rounded-full border border-dashed w-full relative">
              <span v-if="offer.code" class="font-semibold text-gray-800">{{ offer.code }}</span>
              <span v-else class="text-gray-500">Offer not available</span>
            </button>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  // Reactive State
  const activeFilter = ref('allOffer');
  
  const filters = ref([
    { label: 'All Offer', value: 'allOffer' },
    { label: "Today's Best Offer", value: 'bestOffer' },
    { label: 'Upcoming Offer', value: 'upcomingOffer' },
    { label: 'Currently Using', value: 'currentlyOffer' }
  ]);
  
  const offers = ref([
    { title: 'Flat 5% Off On Order', code: 'FGFKG6589895AF', image: 'assets/images/top-stores-icon-1.png', tag: 'allOffer' },
    { title: '25% Off All Furnishings', code: '20 : 21 : 03', image: 'assets/images/top-stores-icon-2.png', tag: 'allOffer' },
    { title: '$30 Off Orders Over $150', code: null, image: 'assets/images/top-stores-icon-3.png', tag: 'allOffer' },
    { title: '10% Off All Apparel', code: null, image: 'assets/images/top-stores-icon-4.png', tag: 'allOffer' }
  ]);
  
  // Computed Property
  const filteredOffers = computed(() => {
    return offers.value.filter(offer => activeFilter.value === 'allOffer' || offer.tag === activeFilter.value);
  });
  </script>
  
  <style scoped>
  button:hover span {
    color: blue;
  }
  </style>
  