<template>
  <section
    class="relative mt-20 bg-gray-100 py-20 px-6 lg:px-24 flex flex-col lg:flex-row items-center lg:gap-x-12"
  >
    <!-- Background Circle -->
    <div
      class="absolute left-0 top-1/4 w-48 h-48 bg-red-100 rounded-full -z-10"
    ></div>

    <!-- Left Text Content -->
    <div class="lg:w-1/2 text-center lg:text-left">
      <h2 class="text-accent text-lg font-semibold">We Are Here</h2>
      <h1 class="text-4xl font-bold text-gray-900 mt-2">
        IT Consultant & <br />
        Outsourcing
      </h1>
      <p class="text-gray-600 mt-4">
        We believe that technology is for every business. <br />
        From roadside stall businesses to publicly listed companies.
        <br />Elevate your business with technology.
      </p>
      <button
        class="mt-6 bg-accent text-white px-6 py-3 rounded-md hover:bg-red-700"
      >
        Contact Us
      </button>
    </div>

    <!-- Right Image Grid -->
    <div class="lg:w-1/2 grid grid-cols-2 gap-2 lg:gap-4 mt-8 lg:mt-0">
      <img
        src="/src/assets/hero-1.png"
        alt="Teamwork"
        class="w-full h-32 lg:h-40 xl:h-52 object-cover object-center"
      />
      <img
        src="/src/assets/hero-2.png"
        alt="Analytics"
        class="w-full h-32 lg:h-40 xl:h-52 object-cover object-center"
      />
      <img
        src="/src/assets/hero-3.png"
        alt="Coding"
        class="w-full h-32 lg:h-40 xl:h-52 object-cover object-center"
      />
      <img
        src="/src/assets/hero-4.png"
        alt="Meeting"
        class="w-full h-32 lg:h-40 xl:h-52 object-cover object-center"
      />
    </div>
  </section>
</template>
