<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, EffectFade } from "swiper/modules";
import type { Swiper as SwiperType } from "swiper";
import 'swiper/css'
import 'swiper/css/effect-fade'

const activeSlide = ref(0);
const textSwiper = ref<SwiperType | null>(null);

const slides = [
  {
    imageUrl: "https://staco-react.vercel.app/assets/bohemian-man-CVN_j-Wi.png",
    testimony:
      "Staco has transformed the way our team collaborates and manages projects. The intuitive interface and powerful features have boosted our productivity and streamlined our workflows. Highly recommended!",
    name: "John Doe",
    position: "Project Manager at XYZ Corp",
  },
  {
    imageUrl: "https://staco-react.vercel.app/assets/quote-img5-DdgwyiXw.png",
    testimony:
      "As a small business owner, Staco has been a game-changer for us. The platform's comprehensive tools for HR management and invoicing have simplified our operations, allowing us to focus on growth and customer satisfaction.",
    name: "Jane Smith",
    position: "Founder & CEO of ABC Ltd",
  },
  {
    imageUrl: "https://staco-react.vercel.app/assets/quote-img2-Bs5ctuYK.png",
    testimony:
      "Staco's email marketing features have significantly improved our outreach efforts. The ability to create targeted campaigns and track performance metrics has helped us engage with our audience more effectively.",
    name: "Emily Johnson",
    position: "Marketing Director at 123 Inc",
  },
  {
    imageUrl: "https://staco-react.vercel.app/assets/quote-img3-CPzHyTHF.png",
    testimony:
      "The web services provided by Staco have been instrumental in enhancing our online presence. The platform's user-friendly design and robust functionality have made it easy for us to manage our digital marketing efforts.",
    name: "Michael Brown",
    position: "Digital Marketing Manager at DEF Co",
  },
  {
    imageUrl: "https://staco-react.vercel.app/assets/quote-img4-DCywOInX.png",
    testimony:
      "Staco's performance management tools have empowered our HR team to effectively monitor and enhance employee productivity. The platform's analytics and reporting features have provided valuable insights for decision-making.", 
    name: "Sarah Williams",
    position: "HR Manager at GHI Enterprises",
  }
];

const onTextSwiper = (swiper: SwiperType): void => {
  textSwiper.value = swiper;
};

const onSlideChange = (swiper: SwiperType): void => {
  activeSlide.value = swiper.activeIndex;
};
</script>

<template>
  <section class="mb-36 py-20">
    <div class="container lg:max-w-300 mx-auto">
      <div class="px-3.75">
        <div
          class="pt-25 pb-12.5 pr-5 grid grid-cols-1 lg:grid-cols-2 gap-7.5 rounded-[30px] shadow-lg bg-white overflow-hidden relative"
        >
          <div class="absolute left-0 top-12 z-0">
            <img src="~/assets/images/arrowBehindImage.png" alt="" />
          </div>
          <div class="absolute left-16.25 top-16 z-0">
            <img
              src="~/assets/images/imageBehind.svg"
              alt="Background Decoration"
            />
          </div>

          <div class="px-3.75 mx-auto max-w-[320px] min-h-[300px] z-10 relative">
            <img
              v-for="(slide, index) in slides"
              :src="slide.imageUrl"
              :key="index + '-img'"
              :alt="slide.name"
              :class="{ hidden: activeSlide !== index }"
              class="w-full h-auto object-contain"
            />
          </div>
          
          <div class="relative z-10">
            <div class="absolute -top-10 left-0 z-5">
              <img src="~/assets/images/imagetag.svg" alt="" />
            </div>
            <Swiper
              :modules="[Autoplay, EffectFade]"
              :space-between="30"
              :effect="'fade'"
              :autoplay="{ delay: 5000, disableOnInteraction: false }"
              class="testimonial-slider"
              @swiper="onTextSwiper"
              @slideChange="onSlideChange"
            >
              <SwiperSlide v-for="(slide, index) in slides" :key="index">
                <div
                  class="bg-white p-5 h-full flex flex-col items-start justify-end"
                >
                  <p class="mb-7.5 text-lg leading-relaxed text-gray-700">
                    "{{ slide.testimony }}"
                  </p>
                  <div class="mt-5">
                    <h3 class="font-bold text-xl text-gray-900">{{ slide.name }}</h3>
                    <span class="text-gray-500">{{ slide.position }}</span>
                  </div>
                </div>
              </SwiperSlide>
            </Swiper>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.testimonial-slider {
  height: 100%;
  min-height: 400px;
}

/* Optional: Custom styling for Swiper */
:deep(.swiper-wrapper) {
  height: 100%;
}

:deep(.swiper-slide) {
  height: auto;
}
</style>