<template>
  <section class="py-20 relative bg-white overflow-hidden">
    <div class="container mx-auto px-6 text-center relative max-w-screen-lg">
      <!-- Gambar (disembunyikan di layar kecil) -->
      <div
        class="relative w-full lg:-translate-x-15 lg:w-3/4 mx-auto hidden md:block"
      >
        <img
          src="/src/assets/about-us.png"
          alt="About"
          class="w-full rounded-2xl xl:max-w-[856px]"
        />
      </div>

      <!-- Kotak Merah (Konten) -->
      <div
        class="bg-accent/90 text-white text-left p-8 sm:p-12 w-full sm:max-w-[90%] sm:mx-auto md:max-w-[320px] mt-6 md:mt-0 md:absolute md:right-6 md:top-1/2 md:transform md:-translate-y-1/2"
      >
        <h3 class="text-2xl sm:text-3xl font-bold">About Us</h3>
        <p class="mt-4 leading-relaxed text-justify">
          As an Information Technology Outsourcing or (IT Outsourcing) company,
          we help your business to grow through qualified human resources.
        </p>
        <RouterLink
          to="/about"
          class="mt-6 bg-white text-accent px-6 py-3 rounded-md font-semibold hover:bg-gray-200 transition w-max block"
        >
          About Our Company
        </RouterLink>
      </div>
    </div>

    <!-- SVG Background -->
    <div class="absolute top-10 -right-4 pointer-events-none">
      <img
        src="/src/components/Vector/service-vector.svg"
        alt="Background Vector"
        class="w-[88px] h-auto max-w-[200px] opacity-50 transform rotate-[5deg]"
      />
    </div>
  </section>
</template>
