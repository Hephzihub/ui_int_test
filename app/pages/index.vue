<script setup lang="ts"></script>

<template>
  <div>
    <HeroSection />

    <CardSection />

    <section class="mb-36">
      <div class="container mx-auto px-4">
        <div class="bg-olive-dark overflow-hidden px-17.5 rounded-[30px] grid grid-cols-1 md:grid-cols-2">
          <div class="pt-14 pb-17.5">
            <h2 class="text-5xl text-white leading-relaxed">
              We are building <br> financial foundations
            </h2>

            <a href="#" class="group bg-olive rounded-[100px] flex items-center justify-center gap-2 px-7.5 py-4 mt-10 hover:bg-olive-medium transition w-fit">
              <span class="text-black group-hover:text-white duration-300 transition">
                Let's Talk
              </span>
              <UIcon name="i-lucide-arrow-right" class="w-5 h-5 text-black group-hover:text-white group-hover:-rotate-45 duration-300 transition"/>
            </a>
          </div>

          <div class="flex items-end justify-end h-full">
            <!-- <NuxtImg
              src="~/assets/images/arrods.svg"
              alt="Arrow Illustration"
              class="object-contain"
            /> -->
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
