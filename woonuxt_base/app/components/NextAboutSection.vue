<!-- components/SectionNextAbout.vue -->
<template>
  <section class="relative w-full overflow-hidden bg-[#FAFAFA] h-[75vh]">
    <div class="grid grid-cols-1 lg:grid-cols-2 h-full">
      <!-- Bal: kép -->
      <div class="relative lg:absolute lg:left-0 lg:h-full lg:w-1/2">
        <img
          src="/img/nextabout.webp"
          alt="Modern automata kétszárnyú kapu meghajtóval"
          class="h-full w-full object-fill"
          loading="eager"
          fetchpriority="high"
          decoding="async"
        />
      </div>

      <!-- Jobb: szöveg -->
      <div class="lg:col-start-2 flex items-center relative z-10 pl-10">
        <div class="container mx-auto px-6 sm:px-12 py-16 lg:py-28 ">
          <h2 style="line-height: 70px;" class="font-['Red_Hat_Display'] font-[700] text-[30px] lg:text-[55px] leading-[1.05] mb-8">
            Kaputechnika <br />
            Profiktól
          </h2>

          <NuxtLink
            to="/"
            style="padding: 20px 48px;" class="text-[20] font-['Red_Hat_Display']  inline-flex items-center justify-center rounded-[12px] text-lg font-semibold text-white bg-[#FD2D2D] hover:bg-red-600 active:bg-blue-700 transition focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-400 focus-visible:ring-offset-2">
            Árajánlat kérése
          </NuxtLink>
        </div>
      </div>
    </div>
  </section>
</template>