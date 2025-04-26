<template>
  <section class="bg-gray-100 pb-4">
    <div
      v-if="showAlert"
      class="relative bg-gradient-to-r from-green-400 to-blue-500 text-white py-2 px-4 sm:px-6 mb-2 flex items-center justify-between shadow-lg rounded-md mx-2 animate-fade-in transition-all duration-300"
    >
      <div class="flex items-center gap-2 sm:gap-3 flex-wrap">
        <span
          class="bg-white text-blue-600 text-[10px] sm:text-xs font-extrabold px-2 sm:px-3 py-0.5 sm:py-1 rounded-full shadow-md uppercase tracking-wide"
        >
          New
        </span>

        <span
          class="text-sm sm:text-base font-semibold tracking-wide drop-shadow-sm text-center sm:text-left"
        >
          Get the Best Online Deals, Coupons & Offers
        </span>
      </div>

      <button
        @click="closeAlert"
        class="ml-2 sm:ml-4 p-2 rounded-full hover:bg-white/20 transition-all"
      >
        <Icon name="mdi:close" class="text-2xl sm:text-3xl" />
      </button>
    </div>

    <BoCarousel />

    <div class="mx-10 px-4 flex flex-col justify-center">
      <div
        class="flex flex-col lg:flex-row justify-between items-center lg:items-center py-6 gap-4"
      >
        <div class="flex-1 flex justify-center lg:justify-start">
          <ul
            class="flex flex-wrap items-center gap-3 bg-white p-2 rounded-full shadow-sm"
          >
            <li
              v-for="(filter, index) in filters"
              :key="index"
              @click="activeFilter = filter.value"
              :class="[
                'cursor-pointer px-4 py-1.5 rounded-full text-sm transition-all duration-200 whitespace-nowrap',
                activeFilter === filter.value
                  ? 'bg-blue-500 text-white'
                  : 'text-gray-700 hover:bg-gray-200',
              ]"
            >
              {{ filter.label }}
            </li>
          </ul>
        </div>

        <div class="flex justify-center lg:justify-end w-full lg:w-auto">
          <div
            class="w-[320px] sm:w-[468px] md:w-[728px] lg:w-[970px] h-[90px] bg-gray-100 flex items-center justify-center border border-dashed border-gray-400 rounded-md"
          >
            <span class="text-gray-500 text-sm">Ads</span>
          </div>
        </div>
      </div>

      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <template v-for="(offer, index) in filteredOffers" :key="index">
          <NuxtLink :to="`/offer-detail/${offer.slug}`">
            <div
              class="max-w-xs p-4 bg-white rounded-xl border border-blue-200 shadow-sm relative text-center space-y-4 transition"
            >
              <div class="flex justify-center mb-4">
                <NuxtImg
                  :src="offer.image_url"
                  :alt="offer.title"
                  class="h-24 object-contain"
                />
              </div>

              <div class="text-xs text-gray-400 mb-1">Bajaj Finserv EMI</div>
              <h3 class="text-gray-800 font-semibold min-h-12 text-sm">
                {{ offer.title.slice(0, 50)
                }}{{ offer.title.length > 50 ? "..." : "" }}
              </h3>

              <div class="flex justify-between items-center mb-3 h-8">
                <div class="flex flex-col">
                  <div
                    class="text-primary-600 font-bold text-lg"
                    v-if="offer.price"
                  >
                    ₹ {{ offer.price }}
                  </div>
                  <div
                    class="text-green-600 text-xs font-semibold bg-green-200 p-1 px-2 rounded-full"
                  >
                    50% OFF
                  </div>
                </div>
                <button
                  class="bg-green-500 text-white px-3 py-1 rounded-md hover:bg-green-600 transition cursor-pointer"
                >
                  Get Deal
                </button>
              </div>

              <div
                class="flex justify-end items-center gap-2 text-gray-400 text-xs"
              >
                <span>About {{ timeAgo(offer.createdAt) }}</span>
              </div>
            </div>
          </NuxtLink>
        </template>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, computed, onMounted } from "vue";
import { timeAgo } from "~/utils/time-ago.ts";

const activeFilter = ref("allOffer");
const showAlert = ref(true);

const filters = ref([
  { label: "All Offer", value: "allOffer" },
  { label: "Today's Best Offer", value: "bestOffer" },
  { label: "Latest", value: "upcomingOffer" },
]);

const { data: offersData, error } = await useAsyncData("offers", async () => {
  const res = await fetch(
    "https://boss-offer-production.up.railway.app/api/posts"
  );
  const json = await res.json();
  return json.data;
});

const offers = computed(() => offersData.value || []);

const filteredOffers = computed(() => {
  return offers.value.filter(
    (offer) =>
      activeFilter.value === "allOffer" || offer.tag === activeFilter.value
  );
});

const closeAlert = () => {
  showAlert.value = false;
};
</script>

<style scoped>
button:hover span {
  color: blue;
}

@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 0.5s ease-out;
}
</style>
