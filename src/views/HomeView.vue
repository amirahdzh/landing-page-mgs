<template>
  <div>
    <!-- Hero Section -->
    <section
      class="px-10 py-16 text-center lg:text-left flex flex-col lg:flex-row items-center gap-10"
    >
      <div class="max-w-lg">
        <h2 class="text-red-600 font-bold text-lg">We Are Here</h2>
        <h1 class="text-4xl font-bold leading-tight mt-2">
          IT Consultant & Outsourcing
        </h1>
        <p class="mt-4 text-gray-700">
          We believe that technology is for every business. From moderate scale
          business, to publicly listed business. Elevate your business with
          technology.
        </p>
        <button class="mt-6 bg-red-600 text-white px-6 py-3 rounded-md">
          Contact Us
        </button>
      </div>
      <div>
        <img
          src="/src/assets/hero-image.png"
          alt="Hero Image"
          class="w-full max-w-xl"
        />
      </div>
    </section>

    <!-- Our Services -->
    <section class="px-10 py-16 text-center">
      <h3 class="text-red-600 font-bold">What We Have</h3>
      <h2 class="text-3xl font-bold">Our Services</h2>
      <div class="mt-10 flex flex-wrap justify-center gap-6">
        <div class="bg-white shadow-md p-6 rounded-lg w-80">
          <h4 class="font-bold text-xl">IT Outsourcing</h4>
          <p class="mt-2 text-gray-700">
            Hire our best IT expert and let us help about your business needs.
          </p>
        </div>
        <div class="bg-white shadow-md p-6 rounded-lg w-80">
          <h4 class="font-bold text-xl">Digital Transformation</h4>
          <p class="mt-2 text-gray-700">
            We offer solutions through our digital transformation services.
          </p>
        </div>
      </div>
    </section>

    <!-- Why MGS -->
    <section class="px-10 py-16 text-center">
      <h3 class="text-red-600 font-bold">Why MGS?</h3>
      <h2 class="text-3xl font-bold">Reason why MGS is the right place</h2>
      <div class="mt-10 flex flex-wrap justify-center gap-6">
        <div class="w-60 text-center">
          <h4 class="font-bold text-lg">Affordable</h4>
          <p class="text-gray-700">We provide affordable modular services.</p>
        </div>
        <div class="w-60 text-center">
          <h4 class="font-bold text-lg">Customized</h4>
          <p class="text-gray-700">We tailor solutions to your needs.</p>
        </div>
        <div class="w-60 text-center">
          <h4 class="font-bold text-lg">Collaborative Process</h4>
          <p class="text-gray-700">We involve you in every step.</p>
        </div>
        <div class="w-60 text-center">
          <h4 class="font-bold text-lg">Continuous Support</h4>
          <p class="text-gray-700">We provide ongoing maintenance.</p>
        </div>
      </div>
    </section>

    <!-- About Us -->
    <section class="relative px-10 py-16">
      <img
        src="/src/assets/hero-image.png"
        alt="About Us"
        class="w-full h-96 object-cover rounded-lg"
      />
      <div
        class="absolute bottom-10 left-10 bg-red-600 text-white p-6 rounded-lg"
      >
        <h3 class="text-xl font-bold">About Us</h3>
        <p class="mt-2 text-sm">
          As an IT Outsourcing company, we help your business grow through
          qualified resources.
        </p>
        <button class="mt-4 bg-white text-red-600 px-4 py-2 rounded-md">
          About Our Company
        </button>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="px-10 py-16 bg-red-600 text-white text-center">
      <h3 class="text-lg font-bold">Our Purpose</h3>
      <h2 class="text-3xl font-bold">Technology Inclusivity</h2>
    </section>

    <!-- Contact Section -->
    <section class="px-10 py-16 grid lg:grid-cols-2 gap-10">
      <div>
        <h3 class="text-red-600 font-bold">Contact Us</h3>
        <h2 class="text-3xl font-bold">Haven't gotten what you want yet?</h2>
        <div class="mt-6 space-y-4">
          <p>📞 024 429 533</p>
          <p>✉️ info@mgsaja.co.id</p>
          <p>📍 Jl. A Yani, Yogyakarta</p>
        </div>
      </div>
      <div class="bg-gray-100 p-6 rounded-lg">
        <input class="w-full p-2 rounded mb-4" type="text" placeholder="Name" />
        <input
          class="w-full p-2 rounded mb-4"
          type="email"
          placeholder="Email"
        />
        <textarea
          class="w-full p-2 rounded mb-4"
          rows="4"
          placeholder="Your Message"
        ></textarea>
        <button class="bg-red-600 text-white px-6 py-3 rounded-md w-full">
          Send
        </button>
      </div>
    </section>
  </div>
</template>
