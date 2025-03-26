<script setup lang="ts">
import { ref, computed } from "vue";
import { RouterLink } from "vue-router";
import { onClickOutside } from "@vueuse/core";

// State untuk dropdown utama
const activeDropdown = ref<string | null>(null);
const servicesDropdownRef = ref(null);
const aboutDropdownRef = ref(null);
const isMenuOpen = ref(false);
const mobileMenuRef = ref(null);

// const isServicesOpen = ref(false);
// const isAboutOpen = ref(false);
const isLanguageOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

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
// Menutup menu saat klik di luar
onClickOutside(mobileMenuRef, () => {
  isMenuOpen.value = false;
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

const activeMobileDropdown = ref<string | null>(null);
const toggleMobileDropdown = (menu: string) => {
  activeMobileDropdown.value =
    activeMobileDropdown.value === menu ? null : menu;
};
</script>

<template>
  <header class="w-full fixed min-h-[80px] z-100 top-0 left-0 right-0 bg-white">
    <div
      class="h-[4rem] px-20 py-10 flex justify-between items-center max-md:px-5"
    >
      <!-- Logo -->
      <RouterLink to="/">
        <img src="/src/assets/main-logo.png" alt="Logo" class="w-32 h-auto" />
      </RouterLink>

      <!-- Desktop Navigation -->
      <nav class="hidden lg:flex items-center gap-10 text-sm font-medium">
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
                    class="text-neutral hover:text-accent whitespace-nowrap"
                  >
                    Independent Staff Augmentation
                  </RouterLink>
                </li>
                <li>
                  <RouterLink
                    to="/team-augmentation"
                    class="text-neutral hover:text-accent"
                  >
                    Team Augmentation
                  </RouterLink>
                  <ul class="ml-5 mt-1 space-y-1">
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="text-neutral hover:text-accent"
                      >
                        IT Managed Services
                      </RouterLink>
                    </li>
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="text-neutral hover:text-accent"
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
                    class="text-neutral hover:text-accent"
                    >Digitisation</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    to="/digitalisation"
                    class="text-neutral hover:text-accent"
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
              class="block p-2 text-neutral hover:text-accent"
              >About MGS</RouterLink
            >
            <RouterLink
              to="/case-study"
              class="block p-2 text-neutral hover:text-accent"
              >Case Study</RouterLink
            >
            <RouterLink
              to="/blog"
              class="block p-2 text-neutral hover:text-accent"
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
              class="cursor-pointer px-4 py-2 text-neutral hover:bg-accent hover:text-white"
            >
              ID
            </div>
            <div
              @click="selectLanguage('EN')"
              class="cursor-pointer px-4 py-2 text-neutral hover:bg-accent hover:text-white"
            >
              EN
            </div>
          </div>
        </div>
      </nav>

      <!-- Hamburger Menu -->
      <button
        @click="toggleMenu"
        class="lg:hidden text-neutral focus:outline-none"
      >
        <i
          :class="isMenuOpen ? 'pi pi-times' : 'pi pi-bars'"
          class="w-8 h-8"
        ></i>
      </button>

      <!-- Mobile Menu -->
      <!-- Mobile Navigation -->
      <div
        v-if="isMenuOpen"
        ref="mobileMenuRef"
        class="absolute top-full right-5 w-full max-w-[300px] bg-white shadow-md rounded-md mt-2 max-lg:block p-3"
      >
        <nav class="flex flex-col space-y-3 text-sm font-semibold">
          <!-- Our Services Dropdown -->
          <div>
            <div
              @click="toggleMobileDropdown('services')"
              class="flex justify-between px-3 py-2 rounded-md cursor-pointer hover:bg-gray-100"
            >
              <p>Our Services</p>
              <i
                :class="
                  activeMobileDropdown === 'services'
                    ? 'pi pi-chevron-up'
                    : 'pi pi-chevron-down'
                "
              ></i>
            </div>
            <div v-if="activeMobileDropdown === 'services'" class="pl-3 mt-1">
              <ul class="space-y-1">
                <li>
                  <RouterLink
                    to="/staff-augmentation"
                    class="hover:text-accent font-normal"
                    >Independent Staff Augmentation</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    to="/team-augmentation"
                    class="hover:text-accent font-normal"
                    >Team Augmentation</RouterLink
                  >
                  <ul class="pl-4 mt-1 space-y-1 text-sm">
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="hover:text-accent font-normal text-neutral"
                        >IT Managed Services</RouterLink
                      >
                    </li>
                    <li>
                      <RouterLink
                        to="/team-augmentation"
                        class="hover:text-accent font-normal text-neutral"
                        >Software Development</RouterLink
                      >
                    </li>
                  </ul>
                </li>
              </ul>
            </div>
          </div>

          <!-- About Dropdown -->
          <div>
            <div
              @click="toggleMobileDropdown('about')"
              class="flex justify-between px-3 py-2 rounded-md cursor-pointer hover:bg-gray-100"
            >
              <p>About</p>
              <i
                :class="
                  activeMobileDropdown === 'about'
                    ? 'pi pi-chevron-up'
                    : 'pi pi-chevron-down'
                "
              ></i>
            </div>
            <div v-if="activeMobileDropdown === 'about'" class="pl-3 mt-1">
              <ul class="space-y-1">
                <li>
                  <RouterLink
                    to="/about-mgs"
                    class="hover:text-accent font-normal"
                    >About MGS</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    to="/case-study"
                    class="hover:text-accent font-normal"
                    >Case Study</RouterLink
                  >
                </li>
                <li>
                  <RouterLink to="/blog" class="hover:text-accent font-normal"
                    >Blog</RouterLink
                  >
                </li>
              </ul>
            </div>
          </div>

          <!-- Career -->
          <RouterLink
            to="/career"
            class="px-3 py-2 rounded-md hover:bg-gray-100"
            >Career</RouterLink
          >

          <!-- Language Switcher -->
          <div>
            <div
              @click="isLanguageOpen = !isLanguageOpen"
              class="flex justify-between px-3 py-2 rounded-md cursor-pointer hover:bg-gray-100"
            >
              <p>Language</p>
              <i
                :class="
                  isLanguageOpen ? 'pi pi-chevron-up' : 'pi pi-chevron-down'
                "
              ></i>
            </div>
            <div v-if="isLanguageOpen" class="pl-3 mt-1">
              <ul class="space-y-1">
                <li
                  @click="selectLanguage('ID')"
                  class="cursor-pointer hover:text-accent"
                >
                  ID
                </li>
                <li
                  @click="selectLanguage('EN')"
                  class="cursor-pointer hover:text-accent"
                >
                  EN
                </li>
              </ul>
            </div>
          </div>
        </nav>
      </div>
    </div>
  </header>
</template>
