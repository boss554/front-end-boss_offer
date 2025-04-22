<template>
  <section class="bg-gray-100 py-6">
    <BoCarousel />

    <div class="max-w-7xl mx-auto px-4">
      <!-- Header and Filters -->
      <div
        class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 md:gap-0 py-6"
      >
        <h3 class="text-xl md:text-2xl font-semibold text-gray-800">
          Popular Offers
        </h3>
        <ul class="flex flex-wrap gap-3 bg-white p-2 rounded-full shadow-sm">
          <li
            v-for="(filter, index) in filters"
            :key="index"
            @click="activeFilter = filter.value"
            :class="[
              'cursor-pointer px-4 py-1.5 rounded-full text-sm transition-all duration-200',
              activeFilter === filter.value
                ? 'bg-blue-500 text-white'
                : 'text-gray-700 hover:bg-gray-200',
            ]"
          >
            {{ filter.label }}
          </li>
        </ul>
      </div>

      <!-- Offers Grid -->
      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <template v-for="(offer, index) in filteredOffers" :key="index">
          <NuxtLink :to="`/offer-detail/${offer.id}`">
            <div
              class="max-w-xs p-4 bg-white rounded-xl border border-blue-200 shadow-sm relative text-center space-y-4"
            >
              <!-- Top Badges -->
              <div class="absolute top-2 left-2">
                <span
                  class="bg-blue-100 text-blue-600 text-sm font-medium px-3 py-1 rounded-full"
                  >Features</span
                >
              </div>
              <div
                class="absolute top-2 right-2 flex items-center gap-1 bg-orange-50 px-2 py-1 rounded-full text-orange-500 text-sm font-semibold"
              >
                <Icon name="mdi-light:star" class="text-base" />
                <span>4.7</span>
              </div>

              <!-- Logo -->
              <NuxtImg
                :src="offer.image_url"
                :alt="offer.title"
                class="w-16 h-16 mx-auto rounded-full bg-white"
              />

              <!-- Title and Description -->
              <div>
                <h3 class="text-gray-800 font-semibold min-h-12">
                  {{ offer.title.slice(0, 50)
                  }}{{ offer.title.length > 50 ? "..." : "" }}
                </h3>
              </div>

              <!-- Expiry -->
              <div
                class="flex items-center justify-center gap-2 text-sm bg-blue-100 text-blue-700 px-3 py-1 rounded-md w-fit mx-auto"
              >
                <Icon name="mdi-light:calendar" class="text-base" />
                <span>Ends : 25/10/25</span>
              </div>
              <button
                class="mt-3 px-5 py-2 rounded-full border border-dashed w-full text-center"
              >
                <span v-if="offer.code" class="font-semibold text-gray-800">
                  {{ offer.code }}
                </span>
                <span v-else class="text-gray-500">Offer not available</span>
              </button>
            </div>
          </NuxtLink>
        </template>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, computed, onMounted } from "vue";

const activeFilter = ref("allOffer");

const filters = ref([
  { label: "All Offer", value: "allOffer" },
  { label: "Today's Best Offer", value: "bestOffer" },
  { label: "Upcoming Offer", value: "upcomingOffer" },
  { label: "Currently Using", value: "currentlyOffer" },
]);

const { data: offersData, error } = await useAsyncData("offers", async () => {
  const res = await fetch("https://boss-offer.onrender.com/api/posts");
  const json = await res.json();
  return json.posts;
});

const offers = computed(() => offersData.value || []);

const filteredOffers = computed(() => {
  return offers.value.filter(
    (offer) =>
      activeFilter.value === "allOffer" || offer.tag === activeFilter.value
  );
});
</script>

<style scoped>
button:hover span {
  color: blue;
}
</style>
