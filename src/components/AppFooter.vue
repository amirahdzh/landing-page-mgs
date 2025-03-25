<template>
  <footer
    class="bg-[#061951] text-white px-[100px] pt-10 pb-10 max-sm:p-10 max-lg:p-10"
  >
    <div class="flex justify-between gap-10 max-md:flex-col items-start">
      <!-- Logo & Description -->
      <div class="w-full lg:w-[300px]">
        <div class="flex items-center space-x-2">
          <img
            src="/src/assets/main-logo-white.png"
            alt="Logo"
            class="w-20 md:w-24 lg:w-28 h-auto"
          />
        </div>
        <p class="mt-4 text-sm leading-relaxed">
          As an Information Technology Outsourcing (IT Outsourcing) company, we
          help your business to grow through qualified human resources.
        </p>
      </div>

      <!-- Links -->
      <div class="flex gap-24 max-lg:gap-10 max-md:flex-col items-start">
        <div class="flex flex-col gap-2 text-[16px] max-sm:gap-3 max-lg:gap-2">
          <p class="font-semibold text-xl mb-6">Services</p>
          <a href="/layanan-kami/it-outsourcing">IT Outsourcing</a>
          <a href="/layanan-kami/transformasi-digital"
            >Digital Transformation</a
          >
          <a href="/layanan-kami/transformasi-digital">Career</a>
        </div>
        <div class="flex flex-col gap-2 text-[16px] max-sm:gap-3 max-lg:gap-2">
          <p class="font-semibold text-xl mb-6">About</p>
          <a href="/layanan-kami/it-outsourcing">MGS</a>
          <a href="/layanan-kami/transformasi-digital">History</a>
          <a href="/layanan-kami/transformasi-digital">Our Team</a>
        </div>
        <div class="flex flex-col gap-2 text-[16px] max-sm:gap-3 max-lg:gap-2">
          <p class="font-semibold text-xl mb-6">Contact</p>
          <a href="/tentang-mgs">Call</a>
          <a href="/kontak">Email</a>
          <a href="/karir">Location</a>
        </div>
      </div>
    </div>

    <div class="h-[1px] bg-white mt-10"></div>

    <!-- Social Media & Sitemap -->
    <div class="pt-6 flex flex-col lg:flex-row justify-between items-center">
      <div class="flex space-x-4">
        <a
          href="#"
          class="p-2 bg-white rounded-md hover:bg-gray-100 transition flex items-center justify-center w-10 h-10"
        >
          <i class="pi pi-linkedin text-xl text-[#061951]"></i>
        </a>
        <a
          href="#"
          class="p-2 bg-white rounded-md hover:bg-gray-100 transition flex items-center justify-center w-10 h-10"
        >
          <i class="pi pi-facebook text-xl text-[#061951]"></i>
        </a>
        <a
          href="#"
          class="p-2 bg-white rounded-md hover:bg-gray-100 transition flex items-center justify-center w-10 h-10"
        >
          <i class="pi pi-instagram text-xl text-[#061951]"></i>
        </a>
        <a
          href="#"
          class="p-2 bg-white rounded-md hover:bg-gray-100 transition flex items-center justify-center w-10 h-10"
        >
          <i class="pi pi-twitter text-xl text-[#061951]"></i>
        </a>
      </div>
      <RouterLink to="/sitemap" class="mt-4 lg:mt-0 text-sm hover:underline"
        >Sitemap</RouterLink
      >
    </div>
  </footer>
</template>
