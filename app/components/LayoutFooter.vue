<script setup lang="ts">
const footerLinks = [
  {
    header: "Products 🔥",
    links: [
      { name: "HR Management", href: "#" },
      { name: "Invoice System", href: "#" },
      { name: "Email Marketing", href: "#" },
      { name: "Web Services", href: "#" },
      { name: "Digital Marketing", href: "#" },
    ],
  },
  {
    header: "Why choose 🌟",
    links: [
      { name: "Customers", href: "#" },
      { name: "Why Staco ?", href: "#" },
      { name: "Book a demo", href: "#" },
    ],
  },
  {
    header: "Resources ❇️",
    links: [
      { name: "Latest Blog", href: "#" },
      { name: "Supports", href: "#" },
      { name: "Knowledgebase", href: "#" },
      { name: "FAQs", href: "#" },
    ],
  },
  {
    header: "Company 💎",
    links: [
      { name: "About", href: "#" },
      { name: "What we do", href: "#" },
      { name: "Contact us", href: "#" },
      { name: "Careers", href: "#" },
    ],
  },
];
</script>

<template>
  <footer class="relative">
    <div class="mb-20 z-30 relative">
      <section class="container mx-auto px-5 max-w-390">
        <div class="bg-darkBg rounded-[30px]">
          <div class="pt-30 pb-17.5">
            <div
              class="container max-w-300 mx-auto px-5 grid grid-cols-1 md:grid-cols-4 gap-10"
            >
              <div class="col-span-1 px-3.75">
                <div class="mb-14">
                  <a href=""></a>
                  <p class="text-[#ffffffb2]">
                    Staco is the dedicated platform for performance management
                    that helps to grow your startup quickly
                  </p>
                </div>
                <div class="flex items-center gap-5">
                  <UIcon
                    name="i-lucide-facebook"
                    class="w-6 h-6 text-white hover:text-blue-600 transition cursor-pointer"
                  />
                  <UIcon
                    name="i-lucide-twitter"
                    class="w-6 h-6 text-white hover:text-blue-400 transition cursor-pointer"
                  />
                  <UIcon
                    name="i-lucide-instagram"
                    class="w-6 h-6 text-white hover:text-pink-500 transition cursor-pointer"
                  />
                  <UIcon
                    name="i-lucide-linkedin"
                    class="w-6 h-6 text-white hover:text-blue-700 transition cursor-pointer"
                  />
                  <UIcon
                    name="i-lucide-youtube"
                    class="w-6 h-6 text-white hover:text-blue-700 transition cursor-pointer"
                  />
                </div>
              </div>
              <div class="col-span-3 px-3.75">
                <div class="grid grid-cols-4">
                  <div
                    v-for="(section, index) in footerLinks"
                    :key="index"
                    class="col-span-1 px-3.75"
                  >
                    <h5 class="text-white text-lg font-bold mb-7.5">
                      {{ section.header }}
                    </h5>
                    <div class="flex flex-col gap-5">
                      <a
                        v-for="(link, linkIndex) in section.links"
                        :key="linkIndex"
                        :href="link.href"
                        class="text-[#b0b8bd] hover:text-white transition"
                      >
                        {{ link.name }}
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="py-5 border-t border-slate-50/25">
            <div
              class="container max-w-300 mx-auto px-5 flex flex-col md:flex-row justify-between items-center"
            >
              <p class="text-[#b0b8bd]">© 2024 Staco. All rights reserved.</p>
              <div class="flex items-center gap-5 mt-3.75 md:mt-0">
                <a href="#" class="text-[#b0b8bd] hover:text-white transition"
                  >Terms and Condition</a
                >
                <a href="#" class="text-[#b0b8bd] hover:text-white transition"
                  >Cookies</a
                >
                <a href="#" class="text-[#b0b8bd] hover:text-white transition"
                  >Privacy Policy</a
                >
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
    <section class="sticky top-0 bottom-20 left-0 w-full my-16">
      <div class="container mx-auto px-5 max-w-300">
        <h6 class="mb-3">Disclaimer:</h6>
        <div>
          <p class="text-sm mb-5 text-black/60">
            There are many variations of passages of Lorem Ipsum available, but
            the majority have suffered alteration in some form, by injected
            humour, or randomised words which don't look even slightly
            believable. If you are going to use a passage of Lorem Ipsum, you
            need to be sure there isn't anything embarrassing hidden in the
            middle of text. All the Lorem Ipsum generators on the Internet tend
            to repeat predefined chunks as necessary.
          </p>

          <p class="text-sm text-black/60">
            Making this the first true generator on the Internet. It uses a
            dictionary of over 200 Latin words, combined handful of model
            sentence structures, to generate which looks reasonable. The
            generated Lorem Ipsum is therefore always
          </p>
        </div>
      </div>
    </section>
  </footer>
</template>
