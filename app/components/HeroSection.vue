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

            <div class="mt-8 flex items-center justify-start gap-7.5 flex-wrap">
              <a
                class="bg-olive-medium text-white px-6 py-3 rounded-[100px] h-15 w-55 mr-4 hover:bg-olive flex items-center justify-center duration-300 transition group"
                href="#"
              >
                <span
                  class="relative h-7 w-32 overflow-hidden flex items-center justify-center *:font-bold"
                >
                  <!-- Initial text (slides up and out on hover) -->
                  <span
                    class="absolute w-full transition-all text-center duration-300 ease-in-out group-hover:-translate-y-8 group-hover:opacity-0"
                  >
                    Get Started
                  </span>

                  <!-- Hidden text (slides up from bottom on hover) -->
                  <span
                    class="absolute w-full text-black text-center transition-all duration-300 ease-in-out translate-y-8 opacity-0 group-hover:translate-y-0 group-hover:opacity-100"
                  >
                    Get Started
                  </span>
                </span>
              </a>
              <a
                class="text-white px-6 py-3 bg-transparent group font-bold flex gap-3.5 items-center transition duration-300 hover:text-olive-medium"
                href="#"
              >
                Let's Talk
                <span class="bg-white/20 group-hover:bg-olive-medium rounded-full flex items-center justify-center transition duration-300 h-7.5 w-7.5">
                  <UIcon name="lucide:chevron-right" class="text-white  transition duration-300 group-hover:-rotate-45" />
                </span>
              </a>
            </div>
          </div>
        </div>
        <div class="ml-auto max-w-118 flex items-center justify-end relative">
          <div class="h-85 relative overflow-hidden rounded-4xl">
            <video class="h-full w-full object-cover" loop autoplay playsinline>
              <source
                src="https://staco-react.vercel.app/assets/h6-video-DaLtBHE1.mp4"
              />
            </video>
            <button
              class="absolute h-12.5 w-12.5 right-7.5 bottom-7.5 bg-white flex items-center justify-center text-olive-medium rounded-full"
            >
              <UIcon name="material-symbols-light:pause" class="w-6 h-6" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
