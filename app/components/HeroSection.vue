<script setup lang="ts">
const words = ["Easier", "Simple", "Secure", "Better", "Accessible"];
const currentIndex = ref(0);
const isAnimating = ref(false);

const currentWord = computed(() => words[currentIndex.value]);

onMounted(() => {
  // Start the animation immediately
  isAnimating.value = true;

  // Change word every 3 seconds
  setInterval(() => {
    // Trigger exit animation
    isAnimating.value = false;

    // After a brief delay, change word and restart animation
    setTimeout(() => {
      currentIndex.value = (currentIndex.value + 1) % words.length;
      isAnimating.value = true;
    }, 300); // 300ms for fade out
  }, 3000); // 3 seconds total duration
});
</script>

<template>
  <section class="relative -mt-28 mb-20 md:mb-36 overflow-hidden bg-darkBg">
    <div class="container lg:max-w-300 mx-auto mt-60 mb-56">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div class="px-3.5">
          <div class="*:text-white">
            <h1 class="mb-4 text-6xl font-bold leading-tight">
              Financial Security Made
              <span class="relative inline-block ml-2">
                <!-- The rotating word -->
                <span
                  :key="currentWord"
                  class="transition-opacity duration-300"
                  :class="isAnimating ? 'opacity-100' : 'opacity-0'"
                >
                  {{ currentWord }}
                </span>

                <!-- Animated underline -->
                <span
                  :key="`underline-${currentWord}`"
                  class="absolute bottom-0 left-0 h-1 bg-linear-to-r from-olive-medium to-olive rounded-full"
                  :class="isAnimating ? 'animate-grow-underline' : 'w-0'"
                ></span>
              </span>
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
                  class="relative h-7 w-32 overflow-hidden flex items-center justify-center *:font-medium"
                >
                  <!-- Initial text (slides up and out on hover) -->
                  <span
                    class="absolute w-full transition-all text-center duration-150 ease-in-out group-hover:-translate-y-8 group-hover:opacity-0"
                  >
                    Get Started
                  </span>

                  <!-- Hidden text (slides up from bottom on hover) -->
                  <span
                    class="absolute w-full text-black text-center transition-all duration-150 ease-in-out translate-y-8 opacity-0 group-hover:translate-y-0 group-hover:opacity-100"
                  >
                    Get Started
                  </span>
                </span>
              </a>
              <a
                class="text-white px-6 py-3 bg-transparent group font-medium flex gap-3.5 items-center transition duration-300 hover:text-olive-medium"
                href="#"
              >
                Let's Talk
                <span
                  class="bg-white/20 group-hover:bg-olive-medium rounded-full flex items-center justify-center transition duration-300 h-7.5 w-7.5"
                >
                  <UIcon
                    name="lucide:chevron-right"
                    class="text-white transition duration-300 group-hover:-rotate-45"
                  />
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

<style scoped>
@keyframes growUnderline {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}

.animate-grow-underline {
  animation: growUnderline 2.7s linear forwards;
}
</style>
