<template>
  <div class="p-6 bg-white text-left">
    <!-- Gunakan gambar jika icon berupa URL -->
    <img :src="icon" alt="Icon" class="w-10 h-10 mx-auto mb-4" />

    <h4 class="text-xl font-semibold relative inline-block">
      {{ title }}
      <!-- <span
        class="absolute left-0 bottom-0 w-full h-1 bg-red-600 opacity-50 blur-md"
      ></span> -->
      <span class="absolute left-0 bottom-0 w-10 h-[4px] bg-red-600"></span>
    </h4>
    <p class="mt-2 text-gray-600">{{ description }}</p>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  icon: string;
  title: string;
  description: string;
}>();
</script>
