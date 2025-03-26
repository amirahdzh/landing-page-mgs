<script setup lang="ts">
import { useFetch } from "@vueuse/core";
import { computed } from "vue";
import WhyCard from "./WhyCard.vue";

// Fetch data from API
const { data, error, isFetching } = useFetch(
  "https://strapi-admin.megagigasolusindo.co.id/api/whies"
).json();

// Default icon dari file lokal
import defaultIcon from "@/components/Vector/why.png";

// Format data untuk ditampilkan
const reasons = computed(() => {
  return (
    data.value?.data.map((item: any) => ({
      icon: defaultIcon, // Gunakan gambar default jika API tidak menyediakan icon
      title: item.title || "No Title",
      description: item.description || "No Description Available",
    })) || []
  );
});
</script>

<template>
  <section class="px-6 py-16 lg:py-24 text-center bg-gray-100">
    <div class="container mx-auto px-6 text-center relative max-w-screen-lg">
      <h2 class="text-red-600 font-semibold">Why MGS?</h2>
      <h3 class="text-4xl font-medium mt-2">
        Reason why MGS is the right place
      </h3>

      <!-- Loading State -->
      <p v-if="isFetching" class="text-gray-500 mt-6">Loading...</p>

      <!-- Error State -->
      <p v-else-if="error" class="text-red-500 mt-6">
        Failed to load data. Please try again.
      </p>

      <!-- Card List -->
      <div v-else class="mt-10 flex flex-wrap justify-center gap-6">
        <WhyCard
          v-for="(reason, index) in reasons"
          :key="index"
          :icon="reason.icon"
          :title="reason.title"
          :description="reason.description"
          class="w-full sm:w-[300px] md:w-[250px] lg:w-[280px]"
        />
      </div>
    </div>
  </section>
</template>
