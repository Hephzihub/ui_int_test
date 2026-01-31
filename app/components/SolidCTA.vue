<script setup lang="ts">
const sectionRef = ref<HTMLElement | null>(null)
const isVisible = ref(false)
const scrollY = ref(0)
const imageOffset = ref(0)

const handleScroll = () => {
  if (!sectionRef.value) return
  
  const rect = sectionRef.value.getBoundingClientRect()
  const windowHeight = window.innerHeight
  
  // Calculate how much of the section is in view
  // Positive when section is in viewport, negative when above/below
  const sectionProgress = (windowHeight - rect.top) / (windowHeight + rect.height)
  
  // Map progress to pixel offset (-100px to 100px range)
  // When scrolling down: image moves up (negative)
  // When scrolling up: image moves down (positive)
  // console.log('Section Progress:', sectionProgress - 0.5)
  // imageOffset.value = (sectionProgress - 0.5) * 200
  // console.log('Translate Progress:', (sectionProgress - 0.5) * 200)
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          isVisible.value = true
          window.addEventListener('scroll', handleScroll)
          handleScroll() // Initial calculation
        } else {
          isVisible.value = false
          window.removeEventListener('scroll', handleScroll)
        }
      })
    },
    {
      threshold: 0.2,
      rootMargin: '0px'
    }
  )

  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }

  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
    if (sectionRef.value) {
      observer.unobserve(sectionRef.value)
    }
  })
})
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
          :class="isVisible ? 'translate-x-0 opacity-100' : '-translate-x-20 opacity-0'"
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