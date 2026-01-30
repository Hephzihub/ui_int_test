<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination, Autoplay } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

const textSwiper = ref(null);
const activeSlide = ref(0);

const slides = [
  {
    title: "Manage team increase productivity",
    description:
      "We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.",
    image:
      "https://staco-react.vercel.app/assets/feature-team1-CkrnjYrI.png",
  },
  {
    title: "Discover Business Growth Solutions",
    description:
      "We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.",
    image:
      "https://staco-react.vercel.app/assets/feature-team2-BkN4ZF3A.png",
  },
  {
    title: "Manage team increase productivity",
    description:
      "We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.",
    image:
      "https://staco-react.vercel.app/assets/feature-team3-rNw9B1sS.png",
  },
];

const onTextSwiper = (swiper) => {
  textSwiper.value = swiper;
};

const onSlideChange = (swiper) => {
  activeSlide.value = swiper.activeIndex;
};

const goToSlide = (index) => {
  if (textSwiper.value) {
    textSwiper.value.slideTo(index);
  }
};
</script>

<template>
  <section class="pb-30 order-2 md:order-1">
    <div class="container max-w-300 mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-2 items-center">
        <div class="px-3.75 order-2 md:order-1">
          <Swiper
            :modules="[Autoplay]"
            :space-between="30"
            :autoplay="{ delay: 5000, disableOnInteraction: false }"
            @swiper="onTextSwiper"
            @slideChange="onSlideChange"
            class="text-slider"
          >
            <SwiperSlide v-for="(slide, index) in slides" :key="index">
              <div class="">
                <span class="text-lg font-bold mb-3 block tracking-[0.2em]"
                  >WHY CHOOSE US</span
                >
                <h2 class="text-[40px] font-bold mb-10 leading-relaxed">
                  {{ slide.title }}
                </h2>

                <p>
                  {{ slide.description }}
                </p>

                <ul class="mt-5 flex flex-row gap-5 flex-wrap max-w-96">
                  <li
                    class="flex flex-row items-center"
                    v-for="(item, index) in 3"
                    :key="index"
                  >
                    <UIcon
                      name="i-lucide-check"
                      class="w-5 h-5 text-green-500 inline-block mr-3"
                    />Reliable Services
                  </li>
                </ul>
              </div>
            </SwiperSlide>
          </Swiper>
        </div>
        <div class="px-3.75 order-1 md:order-2">
          <div class="order-1 md:order-2">
            <div
              class="relative flex items-center justify-center gap-4 h-[500px]"
            >
              <!-- Left Image (Slide 0) -->
              <div
                :class="[
                  'rounded-3xl overflow-hidden transition-all duration-700 ease-in-out cursor-pointer',
                  activeSlide === 0
                    ? 'w-[450px] h-[500px] z-20 opacity-100'
                    : 'w-[200px] h-[500px] z-10 opacity-60 hover:opacity-80',
                ]"
                @click="goToSlide(0)"
              >
                <img
                  :src="slides[0].image"
                  :alt="slides[0].title"
                  class="w-full h-full object-cover"
                />
                <div v-if="activeSlide !== 0" class="absolute inset-0"></div>
              </div>

              <!-- Center Image (Slide 1) -->
              <div
                :class="[
                  'rounded-3xl overflow-hidden transition-all duration-700 ease-in-out cursor-pointer',
                  activeSlide === 1
                    ? 'w-[450px] h-[500px] z-20 opacity-100'
                    : 'w-[200px] h-[500px] z-10 opacity-60 hover:opacity-80',
                ]"
                @click="goToSlide(1)"
              >
                <img
                  :src="slides[1].image"
                  :alt="slides[1].title"
                  class="w-full h-full object-cover"
                />
                <div v-if="activeSlide !== 1" class="absolute inset-0"></div>
              </div>

              <!-- Right Image (Slide 2) -->
              <div
                :class="[
                  'rounded-3xl overflow-hidden transition-all duration-700 ease-in-out cursor-pointer',
                  activeSlide === 2
                    ? 'w-[450px] h-[500px] z-20 opacity-100'
                    : 'w-[200px] h-[500px] z-10 opacity-60 hover:opacity-80',
                ]"
                @click="goToSlide(2)"
              >
                <img
                  :src="slides[2].image"
                  :alt="slides[2].title"
                  class="w-full h-full object-cover"
                />
                <div v-if="activeSlide !== 2" class="absolute inset-0"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.text-slider {
  padding-bottom: 50px;
}
</style>
