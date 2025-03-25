<template>
  <section class="py-20 relative bg-white overflow-hidden">
    <div class="container mx-auto px-6 text-center relative max-w-screen-lg">
      <!-- Gambar -->
      <div class="relative w-full lg:w-3/4">
        <img
          src="/src/assets/about-us.png"
          alt="About"
          class="w-full rounded-2xl xl:max-w-[856px]"
        />
      </div>

      <!-- Kotak Merah (Konten) -->
      <div
        class="bg-accent/90 text-white p-8 lg:p-12 w-full max-w-[400px] absolute right-6 top-1/2 transform -translate-y-1/2"
      >
        <h3 class="text-3xl font-bold">About Us</h3>
        <p class="mt-4 leading-relaxed">
          As an Information Technology Outsourcing or (IT Outsourcing) company,
          we help your business to grow through qualified human resources.
        </p>
        <button
          class="mt-6 bg-white text-red-600 px-6 py-3 rounded-md font-semibold hover:bg-gray-200 transition w-max"
        >
          About Our Company
        </button>
      </div>
    </div>

    <!-- Vector Decoration -->
    <img
      src="/src/components/Vector/service-vector.svg"
      alt="Service Vector"
      class="absolute right-0 bottom-0 hidden lg:block w-1/3 opacity-50"
    />
  </section>
</template>
