<script setup lang="ts">
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";
import HomeView from "./views/HomeView.vue";
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <AppHeader />
    <main class="flex-grow">
      <HomeView />
    </main>
    <AppFooter />
  </div>
</template>
