<script setup lang="ts">
import { ref, computed } from "vue";
import { RouterLink } from "vue-router";
import { onClickOutside } from "@vueuse/core";

// State untuk dropdown utama
const activeDropdown = ref<string | null>(null);
const servicesDropdownRef = ref(null);
const aboutDropdownRef = ref(null);

const toggleDropdown = (menu: string) => {
  activeDropdown.value = activeDropdown.value === menu ? null : menu;
};

// Gunakan refs berbeda untuk mendeteksi klik di luar
onClickOutside(servicesDropdownRef, () => {
  if (activeDropdown.value === "services") activeDropdown.value = null;
});

onClickOutside(aboutDropdownRef, () => {
  if (activeDropdown.value === "about") activeDropdown.value = null;
});

// Class ikon dropdown
const dropdownIconClass = (menu: string) =>
  computed(() => (activeDropdown.value === menu ? "rotate-180" : "rotate-0"));

// State untuk dropdown bahasa
const currentLanguage = ref("EN");
const languageDropdownActive = ref(false);
const languageDropdownRef = ref(null);

const toggleLanguageDropdown = () => {
  languageDropdownActive.value = !languageDropdownActive.value;
};

const selectLanguage = (lang: string) => {
  currentLanguage.value = lang;
  languageDropdownActive.value = false;
};

// Menutup dropdown bahasa saat klik di luar
onClickOutside(languageDropdownRef, () => {
  languageDropdownActive.value = false;
});
</script>

<template>
  <header class="w-full fixed min-h-[80px] z-10 top-0 left-0 right-0 bg-white">
    <div
      class="h-[4rem] px-20 py-10 flex justify-between items-center max-md:px-5"
    >
      <!-- Logo -->
      <RouterLink to="/">
        <img src="/src/assets/main-logo.png" alt="Logo" class="w-32 h-auto" />
      </RouterLink>

      <!-- Navigation -->
      <nav class="flex items-center gap-10 text-sm font-medium max-lg:hidden">
        <!-- Our Services Dropdown -->
        <div class="relative" ref="servicesDropdownRef">
          <div
            @click.stop="toggleDropdown('services')"
            class="flex items-center gap-2 cursor-pointer"
          >
            <p>Our Services</p>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="17"
              viewBox="0 0 16 17"
              class="transition-transform duration-300"
              :class="dropdownIconClass('services').value"
            >
              <path d="M12 6.5L8 10.5L4 6.5" stroke="#1F1F1F"></path>
            </svg>
          </div>

          <!-- Mega Menu for Services -->
          <div
            v-if="activeDropdown === 'services'"
            class="absolute left-1/2 -translate-x-1/2 mt-10 w-[600px] bg-white shadow-lg rounded-lg p-6 grid grid-cols-2 gap-6 border border-gray-200"
          >
            <div>
              <h3
                class="font-bold text-lg text-gray-900 hover:text-accent mb-2 text-start"
              >
                IT Outsourcing
              </h3>
              <ul class="list-disc list-inside space-y-2">
                <li>
                  <RouterLink
                    to="/staff-augmentation"
                    class="text-gray-700 hover:text-accent whitespace-nowrap"
                  >
                    Independent Staff Augmentation
                  </RouterLink>
                </li>
                <li>
                  <RouterLink
                    to="/team-augmentation"
                    class="text-gray-700 hover:text-accent"
                  >
                    Team Augmentation
                  </RouterLink>
                  <ul class="ml-5 mt-1 space-y-1">
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="text-gray-500 hover:text-accent"
                      >
                        IT Managed Services
                      </RouterLink>
                    </li>
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="text-gray-500 hover:text-accent"
                      >
                        Software Development
                      </RouterLink>
                    </li>
                  </ul>
                </li>
              </ul>
            </div>
            <div>
              <h3
                class="font-bold text-lg text-gray-900 hover:text-accent mb-2"
              >
                Digital Transformation
              </h3>
              <ul class="list-disc list-inside space-y-2">
                <li>
                  <RouterLink
                    to="/digitisation"
                    class="text-gray-700 hover:text-accent"
                    >Digitisation</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    to="/digitalisation"
                    class="text-gray-700 hover:text-accent"
                    >Digitalisation</RouterLink
                  >
                </li>
              </ul>
            </div>
          </div>
        </div>

        <!-- About Dropdown -->
        <div class="relative" ref="aboutDropdownRef">
          <div
            @click.stop="toggleDropdown('about')"
            class="flex items-center gap-2 cursor-pointer text-gray-900"
          >
            <p>About</p>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="17"
              viewBox="0 0 16 17"
              class="transition-transform duration-300"
              :class="dropdownIconClass('about').value"
            >
              <path d="M12 6.5L8 10.5L4 6.5" stroke="#1F1F1F"></path>
            </svg>
          </div>

          <!-- Dropdown Menu for About -->
          <div
            v-if="activeDropdown === 'about'"
            class="absolute left-1/2 -translate-x-1/2 mt-10 w-40 bg-white shadow-lg p-3 rounded-lg border border-gray-200"
          >
            <RouterLink
              to="/about-mgs"
              class="block p-2 text-gray-700 hover:text-accent"
              >About MGS</RouterLink
            >
            <RouterLink
              to="/case-study"
              class="block p-2 text-gray-700 hover:text-accent"
              >Case Study</RouterLink
            >
            <RouterLink
              to="/blog"
              class="block p-2 text-gray-700 hover:text-accent"
              >Blog</RouterLink
            >
          </div>
        </div>

        <!-- Career Link -->
        <RouterLink to="/career" class="text-gray-900">Career</RouterLink>

        <!-- Language Switcher Dropdown -->
        <div class="relative" ref="languageDropdownRef">
          <div
            @click.stop="toggleLanguageDropdown"
            class="flex items-center gap-2 cursor-pointer text-gray-900 border border-gray-300 rounded-md px-3 py-1"
          >
            <p>{{ currentLanguage }}</p>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="12"
              height="12"
              viewBox="0 0 12 12"
              class="transition-transform duration-300"
              :class="languageDropdownActive ? 'rotate-180' : 'rotate-0'"
            >
              <path
                d="M2 4L6 8L10 4"
                stroke="#1F1F1F"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>

          <!-- Language Options Dropdown -->
          <div
            v-if="languageDropdownActive"
            class="absolute right-0 mt-2 w-28 bg-white shadow-lg rounded-md border border-gray-200"
          >
            <div
              @click="selectLanguage('ID')"
              class="cursor-pointer px-4 py-2 text-gray-700 hover:bg-accent hover:text-white"
            >
              ID
            </div>
            <div
              @click="selectLanguage('EN')"
              class="cursor-pointer px-4 py-2 text-gray-700 hover:bg-accent hover:text-white"
            >
              EN
            </div>
          </div>
        </div>
      </nav>
    </div>
  </header>
</template>
