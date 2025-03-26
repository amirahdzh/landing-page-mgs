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
    <!-- Gunakan gambar jika icon adalah URL -->
    <img
      v-if="icon && icon.startsWith('http')"
      :src="icon"
      alt="Service Icon"
      class="w-14 h-14 mb-4"
    />

    <!-- Gunakan default image jika icon tidak ada -->
    <img
      v-else-if="!icon || icon === ''"
      src="/src/assets/home/why-us.png"
      alt="Default Icon"
      class="w-14 h-14 mb-4"
    />

    <!-- Gunakan PrimeIcon jika icon bukan URL -->
    <i v-else :class="['text-4xl text-[#061951]', icon]" class="mb-4"></i>

    <h3 class="text-lg font-semibold text-gray-900">{{ title }}</h3>

    <!-- Garis merah horizontal -->
    <div class="flex items-center gap-2 mt-2">
      <div class="w-12 h-1 bg-red-600"></div>
      <div class="w-36 h-1 bg-red-600"></div>
    </div>

    <p class="text-gray-600 text-sm text-left mt-3 leading-relaxed">
      {{ description }}
    </p>
  </div>
</template>
