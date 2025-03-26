<template>
  <div class="p-6 bg-white text-left">
    <!-- Gunakan gambar jika icon berupa URL -->
    <img :src="icon" alt="Icon" class="w-10 h-10 mx-auto mb-4" />

    <h4 class="text-xl font-semibold relative inline-block">
      {{ title }}

      <span
        class="absolute left-0 bottom-[-8px] h-[6px] w-32 bg-gradient-to-r from-accent to-transparent"
      ></span>
    </h4>

    <p class="mt-6 text-neutral">{{ description }}</p>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  icon: string;
  title: string;
  description: string;
}>();
</script>
