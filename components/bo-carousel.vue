<template>
  <div class="bg-transparent">
    <Carousel v-bind="config">
      <Slide v-for="image in images" :key="image.id" class="h-40 md:h-80">
        <NuxtImg
          :src="image.url"
          class="rounded-lg w-full h-full object-cover"
          :alt="image.title"
        />
      </Slide>

      <template #addons>
        <Navigation class="!bg-[rgba(255,255,255,0.7)] !rounded-full" />
      </template>
    </Carousel>
  </div>
</template>

<script setup>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";

const images = Array.from({ length: 10 }, (_, index) => ({
  id: index + 1,
  url: `https://picsum.photos/seed/${Math.random()}/800/600`,
  title: "Test",
}));

const config = {
  itemsToShow: 2,
  gap: 5,
  autoplay: 4000,
  wrapAround: true,
  pauseAutoplayOnHover: true,
};
</script>
<style scoped></style>
