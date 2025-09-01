<!-- components/SectionReferencesArticles.vue -->
<template>
  <section class="py-16 sm:py-24">
    <div class="container mx-auto px-6 sm:px-12">
      <div class="grid gap-12 lg:grid-cols-5">
        <!-- Referenciák (60%) -->
        <div class="lg:col-span-3 mr-10">
          <h2 class="font-['Red_Hat_Display'] font-[700] text-[30px] lg:text-[40px] mb-6">Referenciák</h2>
          <img src="/img/ref.webp" alt="Referencia kapu" class="w-full h-[320px] sm:h-[420px] object-cover rounded-[20px]" loading="lazy" decoding="async" />
        </div>

        <!-- Cikkek (40%) -->
        <div class="lg:col-span-2">
          <h2 class="font-['Red_Hat_Display'] font-[700] text-[30px] lg:text-[40px] mb-6">Cikkek</h2>
          <div class="grid gap-6 sm:grid-cols-2">
            <!-- 1 -->
            <article>
              <img src="/img/ref.webp" alt="Milyen kapunyitó motort válasszak?" class="w-full h-[160px] object-cover rounded-[16px]" loading="lazy" />
              <h3 class="mt-3 font-['Montserrat'] text-[16px] font-[600]">Milyen kapunyitó motort válasszak?</h3>
            </article>
            <!-- 2 -->
            <article>
              <img
                src="/img/ref.webp"
                alt="5 jel, hogy ideje lecserélni a régi kapurendszerét"
                class="w-full h-[160px] object-cover rounded-[16px]"
                loading="lazy" />
              <h3 class="mt-3 font-['Montserrat'] text-[16px] font-[600]">5 jel, hogy ideje lecserélni a régi kapurendszerét</h3>
            </article>
            <!-- 3 -->
            <article>
              <img
                src="/img/ref.webp"
                alt="WiFi-s kapunyitók: kényelmes vezérlés okoseszközökről"
                class="w-full h-[160px] object-cover rounded-[16px]"
                loading="lazy" />
              <h3 class="mt-3 font-['Montserrat'] text-[16px] font-[600]">WiFi-s kapunyitók: kényelmes vezérlés okoseszközökről</h3>
            </article>
            <!-- 4 -->
            <article>
              <img src="/img/ref.webp" alt="A legjobb rendszerek" class="w-full h-[160px] object-cover rounded-[16px]" loading="lazy" />
              <h3 class="mt-3 font-['Montserrat'] text-[16px] font-[600]">A legjobb rendszerek</h3>
            </article>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>