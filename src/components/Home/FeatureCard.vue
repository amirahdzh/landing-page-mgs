<template>
  <div class="text-center p-6 shadow-md rounded-lg bg-white">
    <h4 class="text-xl font-semibold">{{ title }}</h4>
    <p class="text-gray-600 mt-2">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
});
</script>
