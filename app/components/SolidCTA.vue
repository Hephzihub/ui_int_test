<script setup lang="ts">
const sectionRef = ref<HTMLElement | null>(null);
const isVisible = ref(false);
const scrollY = import.meta.client ? useWindowScroll().y : ref(0);
const imageOffset = ref(0);

watch(scrollY, (newScrollY) => {
  if (sectionRef.value && import.meta.client) {
    const offset = sectionRef.value.offsetTop - window.innerHeight / 2;

    const x = offset
    const z = offset + window.innerHeight / 2
    let y = 250 - ((newScrollY -  x) / (z - x)) * 250
    y = Math.max(0, Math.min(250, y));
    imageOffset.value = y
  }
})

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          isVisible.value = true;
        } else {
          isVisible.value = false;
        }
      });
    },
    {
      threshold: 0.2,
      rootMargin: "0px",
    },
  );

  if (sectionRef.value) {
    observer.observe(sectionRef.value);
  }

  onUnmounted(() => {
    if (sectionRef.value) {
      observer.unobserve(sectionRef.value);
    }
  });
});
</script>

<template>
  <section ref="sectionRef" class="mb-36">
    <div class="container lg:max-w-300 mx-auto px-4">
      <div
        class="bg-olive-dark overflow-hidden px-17.5 rounded-[30px] grid grid-cols-1 md:grid-cols-2"
      >
        <!-- Left Content - Slides in from left -->
        <div
          class="pt-14 pb-17.5 transition-all duration-1000 ease-out"
          :class="
            isVisible
              ? 'translate-x-0 opacity-100'
              : '-translate-x-20 opacity-0'
          "
        >
          <h2 class="text-5xl text-white leading-relaxed">
            We are building <br />
            financial foundations
          </h2>

          <a
            href="#"
            class="group bg-olive rounded-[100px] flex items-center justify-center gap-2 px-7.5 py-4 mt-10 hover:bg-olive-medium transition w-fit"
          >
            <span
              class="text-black group-hover:text-white duration-300 transition"
            >
              Let's Talk
            </span>
            <UIcon
              name="i-lucide-arrow-right"
              class="w-5 h-5 text-black group-hover:text-white group-hover:-rotate-45 duration-300 transition"
            />
          </a>
        </div>

        <!-- Right Image - Parallax scroll effect -->
        <div
          class="flex items-end justify-end h-full transition-all duration-1000 ease-out delay-200"
        >
          <img
            src="~/assets/images/arrows.svg"
            alt="Arrow Illustration"
            class="object-contain transition-transform translate-y-0 duration-300 ease-out"
            :style="{ transform: `translateY(${imageOffset}px)` }"
          />
        </div>
      </div>
    </div>
  </section>
</template>
