<script setup lang="ts">
const IconUsed = resolveComponent('IconUsed')
const IconClean = resolveComponent('IconClean')
const IconBest = resolveComponent('IconBest')

const cardData = [
  {
    icon: IconUsed,
    title: 'Used Advance Technology',
    description:
      'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    icon: IconClean,
    title: 'Clean design & Typography',
    description:
      'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    icon: IconBest,
    title: 'Best customer support',
    description:
      'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  }
]
</script>

<template>
<section class="pb-24.5">
  <div class="container lg:max-w-300 px-3.5 mx-auto">
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-y-7.5">
      <!-- duplicate 3 -->
      <div v-for="(item, index) in cardData" :key="index" class="group px-3.5">
        <div class="px-7.5 py-10 rounded-lg bg-[#eceff1]">
          <div class="mb-8">
            <component :is="item.icon"  class="w-12 h-12"/>
          </div>
          <h5 class="text-black text-lg font-bold pb-5">{{ item.title }}</h5>
          <p class="mb-16 text-[#444444]">
            {{ item.description }}
          </p>

          <div>
            <a :href="item.link" class="flex justify-between items-center gap-5">
              <span class="group-hover:text-green-500 duration-300 transition">Learn More</span>
              <div class="bg-[#0000001a] h-10 w-10 flex items-center justify-center rounded-full group-hover:bg-green-500 duration-300 transition">
                <UIcon name="i-lucide-arrow-right" class="w-5 h-5 text-black group-hover:text-white group-hover:-rotate-45 duration-300 transition" />
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
</template>