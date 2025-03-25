<script setup lang="ts">
defineProps<{
  icon: string;
  title: string;
  description: string;
}>();
</script>

<template>
  <div
    class="border rounded-xl p-8 shadow-sm hover:shadow-md transition bg-white flex flex-col items-start"
  >
    <img :src="icon" alt="Service Icon" class="w-14 h-14 mb-4" />
    <h3 class="text-lg font-semibold text-gray-900">{{ title }}</h3>

    <!-- Garis merah horizontal (sejajar) -->
    <div class="flex items-center gap-2 mt-2">
      <div class="w-12 h-1 bg-red-600"></div>
      <div class="w-36 h-1 bg-red-600"></div>
    </div>

    <p class="text-gray-600 text-sm text-left mt-3 leading-relaxed">
      {{ description }}
    </p>
  </div>
</template>
