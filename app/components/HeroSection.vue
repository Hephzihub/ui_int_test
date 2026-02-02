<script setup lang="ts"></script>

<template>
  <section class="relative -mt-28 mb-20 md:mb-36 overflow-hidden bg-darkBg">
    <div class="container lg:max-w-300 mx-auto mt-60 mb-56">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div class="px-3.5">
          <div class="*:text-white">
            <h1 class="mb-4 text-6xl font-bold leading-tight">
              Financial Security Made <span>Easier</span>
            </h1>

            <p>
              Staco is the dedicated platform for human management that helps to
              grow your startup business quickly
            </p>

            <div class="mt-8">
              <button
                class="bg-blue-600 text-white px-6 py-3 rounded-md mr-4 hover:bg-blue-700 transition"
              >
                Get Started
              </button>
              <button
                class="bg-gray-200 text-gray-800 px-6 py-3 rounded-md hover:bg-gray-300 transition"
              >
                Learn More
              </button>
            </div>
          </div>
        </div>
        <div class="ml-auto max-w-118 flex items-center justify-end relative">
          <div class="h-85 relative overflow-hidden rounded-4xl">
            <video class="h-full w-full object-cover" loop autoplay playsinline>
              <source src="https://staco-react.vercel.app/assets/h6-video-DaLtBHE1.mp4">
            </video>
            <button class="absolute h-12.5 w-12.5 right-7.5 bottom-7.5 bg-white flex items-center justify-center text-olive-medium rounded-full">
              <UIcon name="material-symbols-light:pause" class="w-6 h-6"/>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
