<!-- components/Hero.vue -->
<template>
    <section class="relative overflow-hidden bg-[#FAFAFA] h-[75vh]">
      <div class="container mx-auto grid lg:grid-cols-2 h-full">
        <!-- Left: szöveg + gomb -->
        <div class="flex flex-col justify-center bg-[#FAFAFA] px-6 sm:px-12 py-16 lg:py-28 text-left">
            <h1 class="pr-10  font-['Red_Hat_Display'] text-[30px] lg:text-[55px]" style="color: var(--Dark, #242424); font-style: normal; font-weight: 700;">
            Automata Kapuk
            <br class="hidden sm:block" />
            és Garázskapuk
          </h1>
          
          <div class="mt-10">
            <NuxtLink
              to="/products"
              style="padding: 20px 48px;" class="text-[20] font-['Red_Hat_Display']  inline-flex items-center justify-center rounded-[12px] text-lg font-semibold text-white bg-[#4285F4] hover:bg-blue-600 active:bg-blue-700 transition focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-400 focus-visible:ring-offset-2"
            >
              Termékek
            </NuxtLink>
          </div>
        </div>
  
        <!-- Right: kép beépített árnyékkal -->
        <div class="relative lg:absolute lg:right-0 lg:h-full lg:w-1/2">
          <img
            src="/img/hero.webp"
            alt="Modern automata kétszárnyú kapu meghajtóval"
            class="h-full w-full object-fill"
            loading="eager"
            fetchpriority="high"
            decoding="async"
          />
        </div>
      </div>
    </section>
  </template>