<script setup lang="ts">
const headerGlassy = ref<HTMLElement | null>(null);
const isHovering = ref(false);
const activeLink = ref("Home");

const navItems = [
  { name: "Home", href: "#" },
  { name: "About", href: "#" },
  { name: "Services", href: "#" },
  { name: "Contact", href: "#" },
];

const handleMouseEnter = (event: MouseEvent, itemName: string) => {
  if (!headerGlassy.value) return;

  isHovering.value = true;
  const target = event.currentTarget as HTMLElement;
  const linkRect = target.getBoundingClientRect();
  const containerRect = headerGlassy.value.getBoundingClientRect();

  const left = linkRect.left - containerRect.left;
  const width = linkRect.width;

  // Update CSS custom properties for animation
  headerGlassy.value.style.setProperty("--target-left", `${left}px`);
  headerGlassy.value.style.setProperty("--target-width", `${width}px`);
  headerGlassy.value.setAttribute("data-hover", "true");
};

const handleMouseLeave = () => {
  setTimeout(() => {
    if (!isHovering.value && headerGlassy.value) {
      headerGlassy.value.removeAttribute("data-hover");
    }
  }, 50);
};

const handleNavMouseLeave = () => {
  isHovering.value = false;
  if (headerGlassy.value) {
    headerGlassy.value.removeAttribute("data-hover");
  }
};

const setActiveLink = (name: string) => {
  activeLink.value = name;
};
</script>

<template>
  <header class="sticky top-0 z-50 py-4 hidden md:block">
    <div class="container mx-auto px-4">
      <div
        class="p-1 rounded-full bg-linear-to-br from-white/10 to-white/5 shadow-2xl w-fit mx-auto"
      >
        <div
          ref="headerGlassy"
          class="glassy-header relative bg-gray-800/60 backdrop-blur-md rounded-full p-2 overflow-hidden"
        >
          <div class="glassy-background"></div>

          <nav
            class="relative z-10 flex gap-2"
            @mouseleave="handleNavMouseLeave"
          >
            <a
              v-for="item in navItems"
              :key="item.name"
              :href="item.href"
              :class="[
                'relative px-8 py-4 rounded-full font-medium text-base whitespace-nowrap transition-all duration-300',
                activeLink === item.name
                  ? 'bg-linear-to-br from-gray-100 to-gray-200 text-gray-900 shadow-lg'
                  : 'text-white/70',
              ]"
              @mouseenter="handleMouseEnter($event, item.name)"
              @mouseleave="handleMouseLeave"
              @click.prevent="setActiveLink(item.name)"
            >
              {{ item.name }}
            </a>
          </nav>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped>
.glassy-header {
  --target-left: 8px;
  --target-width: 100%;
}

.glassy-background {
  position: absolute;
  top: 8px;
  left: 8px;
  right: 8px;
  bottom: 8px;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.15) 0%,
    rgba(255, 255, 255, 0.08) 100%
  );
  border-radius: 9999px;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 0;
  opacity: 0.5;
  pointer-events: none;
}

.glassy-header:not([data-hover]) .glassy-background {
  left: 8px;
  right: 8px;
  width: auto;
  opacity: 0.5;
}

.glassy-header[data-hover="true"] .glassy-background {
  left: var(--target-left);
  width: var(--target-width);
  right: auto;
  opacity: 0.8;
}

.glassy-header::after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 9999px;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  pointer-events: none;
}

@media (max-width: 768px) {
  nav {
    flex-direction: column;
    gap: 0.5rem;
  }

  nav a {
    padding: 0.75rem 1.5rem;
    text-align: center;
  }
}
</style>
