<script setup lang="ts">
const props = defineProps<{
  flipped: boolean
  disabled?: boolean
}>()
</script>

<template>
  <!-- Flip button component that can serve as link or button -->
  <button
    :class="[
      'relative w-40 h-12 perspective',
      disabled ? 'cursor-not-allowed opacity-50' : 'cursor-pointer'
    ]"
    :disabled="disabled"
    @click="$emit('click')"
  >
    <div
      class="absolute w-full h-full transition-transform duration-500 transform-style-preserve-3d"
      :class="{
        'rotate-y-180': flipped
      }"
    >
      <!-- Front side -->
      <div
        class="absolute w-full h-full backface-hidden flex items-center justify-center bg-blue-600 text-white rounded-lg"
      >
        <slot name="front">Front</slot> 
      </div>
      <!-- Back side -->
      <div
        class="absolute w-full h-full backface-hidden flex items-center justify-center bg-green-600 text-white rounded-lg rotate-y-180"
      >
        <slot name="back">Back</slot>
      </div>
    </div>
  </button>
</template>