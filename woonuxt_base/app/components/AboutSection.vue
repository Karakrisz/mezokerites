<!-- components/SectionSmartGates.vue -->
<template>
  <section class="py-14 sm:py-20 mt-10">
    <div class="container mx-auto px-6 sm:px-12">
      <div class="grid lg:grid-cols-2 items-center rounded-[24px] bg-[#F7F7F7]">
        <!-- Szöveg -->
        <div class="p-8 sm:p-12 mb-10">
          <h2 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] font-[600] text-[30px] lg:text-[38px] text-gray-900">
            Mobilról vezérelhető kapuk
          </h2>
          <p style="color: var(--Dark, #242424)" class="mt-4 text-gray-700 leading-relaxed font-['Red_Hat_Display'] text-[16px]">
            A mobilról vezérelhető kapuk a modern otthonok és vállalkozások elengedhetetlen kényelmi megoldásai közé tartoznak. Egyetlen érintéssel nyithatja
            vagy zárhatja kapuját, bárhol is tartózkodik – legyen az otthon, munkahely vagy akár nyaralás. Az okoseszközökkel integrálható rendszerek nemcsak
            praktikusak, hanem <strong>biztonságosak</strong> és <strong> energiatakarékosak</strong> is.
          </p>

          <NuxtLink to="/" class="mt-6 inline-flex items-center gap-2 text-gray-900 font-medium group">
            <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 48 48" fill="none">
              <path d="M7.5 24H40.5" stroke="#242424" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" />
              <path d="M27 10.5L40.5 24L27 37.5" stroke="#242424" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </NuxtLink>
        </div>

        <!-- Kép -->
        <div class="relative">
          <img
            src="/img/wifi.png"
            alt="Kapunyitás mobilról Wi-Fi kapcsolaton"
            class="relative lg:-mr-[66px] lg:h-[500px] object-contain mx-auto lg:mx-0"
            style="display: block; margin: auto; margin-top: -59px"
            loading="lazy"
            decoding="async" />
        </div>
      </div>
    </div>
  </section>
  <section class="py-16 sm:py-24">
    <div class="container mx-auto px-6 sm:px-12">
      <div class="grid gap-10 lg:grid-cols-3 lg:gap-12 items-start">
        <!-- BAL: cím + 4 feature -->
        <div class="lg:col-span-2">
          <h2 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] tracking-tight text-gray-900 font-[700] text-[30px] lg:text-[40px]">
            Miért válasszon minket?
          </h2>

          <div class="mt-10 grid gap-10 sm:grid-cols-2">
            <!-- 1. Megbízható márkák -->
            <div class="flex items-start gap-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 64 64" fill="none">
                <path
                  d="M54 28V14C54 13.4696 53.7893 12.9609 53.4142 12.5858C53.0391 12.2107 52.5304 12 52 12H12C11.4696 12 10.9609 12.2107 10.5858 12.5858C10.2107 12.9609 10 13.4696 10 14V28C10 52 32 58 32 58C32 58 54 52 54 28Z"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path d="M22 34L28 40L42 26" stroke="#343330" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <div>
                <h3 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] font-[600] text-[30px] lg:text-[30px]">Megbízható márkák</h3>
                <p style="color: var(--Dark, #242424)" class="mt-2 font-[600] text-[16px] font-['Red_Hat_Display']">
                  Kizárólag bevált, prémium gyártókkal dolgozunk, mint a CAME, DITEC vagy EuroDoor.
                </p>
              </div>
            </div>

            <!-- 2. Egyedi tervezés -->
            <div class="flex items-start gap-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 64 64" fill="none">
                <path
                  d="M41 32.415L49.945 37.7975C50.1739 37.9387 50.4395 38.0091 50.7083 37.9999C50.9771 37.9908 51.2372 37.9024 51.4559 37.7458C51.6747 37.5893 51.8423 37.3717 51.9377 37.1202C52.0332 36.8688 52.0523 36.5948 51.9925 36.3325L49.56 26.285L57.52 19.565C57.7246 19.3926 57.8731 19.1631 57.9466 18.9059C58.02 18.6487 58.0151 18.3754 57.9325 18.1209C57.8498 17.8665 57.6931 17.6425 57.4825 17.4776C57.2719 17.3126 57.0169 17.2143 56.75 17.195L46.3025 16.3675L42.2775 6.83251C42.171 6.58539 41.9944 6.37487 41.7696 6.22697C41.5448 6.07906 41.2816 6.00024 41.0125 6.00024C40.7434 6.00024 40.4802 6.07906 40.2554 6.22697C40.0306 6.37487 39.854 6.58539 39.7475 6.83251L35.7225 16.3675L25.275 17.195C25.0072 17.212 24.7505 17.3088 24.5381 17.4728C24.3256 17.6369 24.1672 17.8608 24.083 18.1156C23.9989 18.3705 23.9929 18.6447 24.0659 18.903C24.1388 19.1613 24.2874 19.3919 24.4925 19.565L32.4525 26.285L30 36.3325C29.9403 36.5948 29.9593 36.8688 30.0548 37.1202C30.1503 37.3717 30.3179 37.5893 30.5366 37.7458C30.7554 37.9024 31.0155 37.9908 31.2843 37.9999C31.5531 38.0091 31.8186 37.9387 32.0475 37.7975L41 32.415Z"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path d="M18.9375 31.0625L6 44" stroke="#343330" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
                <path d="M21.9 46.1001L10 58.0001" stroke="#343330" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
                <path d="M37.51 48.49L28 58" stroke="#343330" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <div>
                <h3 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] font-[600] text-[30px] lg:text-[30px]">Egyedi tervezés</h3>
                <p style="color: var(--Dark, #242424)" class="mt-2  font-[600] text-[16px] font-['Red_Hat_Display']">
                  Minden kaputechnikai megoldásunk az Ön igényeire szabva készül, a felméréstől a kivitelezésig.
                </p>
              </div>
            </div>

            <!-- 3. Telepítő partnerek -->
            <div class="flex items-start gap-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 64 64" fill="none">
                <path
                  d="M21 40C28.1797 40 34 34.1797 34 27C34 19.8203 28.1797 14 21 14C13.8203 14 8 19.8203 8 27C8 34.1797 13.8203 40 21 40Z"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path
                  d="M3.25 49C5.29296 46.21 7.96481 43.9409 11.0488 42.3768C14.1328 40.8127 17.542 39.9976 21 39.9976C24.458 39.9976 27.8672 40.8127 30.9512 42.3768C34.0352 43.9409 36.707 46.21 38.75 49"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path
                  d="M43 40C46.4582 39.9969 49.8684 40.8105 52.9528 42.3744C56.0372 43.9383 58.7087 46.2085 60.75 49"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path
                  d="M39.655 14.435C41.4419 13.9608 43.3094 13.8731 45.1328 14.1779C46.9563 14.4826 48.6938 15.1728 50.2293 16.2024C51.7649 17.2319 53.0632 18.5772 54.0376 20.1483C55.012 21.7194 55.64 23.4803 55.8799 25.3134C56.1197 27.1465 55.9659 29.0097 55.4285 30.7787C54.8911 32.5476 53.9826 34.1816 52.7636 35.5715C51.5447 36.9615 50.0433 38.0755 48.3596 38.8391C46.6759 39.6028 44.8488 39.9985 43 40"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
              </svg>
              <div>
                <h3 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] font-[600] text-[30px] lg:text-[30px]">Telepítő partnerek</h3>
                <p style="color: var(--Dark, #242424)" class="mt-2  font-[600] text-[16px] font-['Red_Hat_Display']">
                  Országos hálózatunk tapasztalt szakemberei gyors és precíz munkát garantálnak.
                </p>
              </div>
            </div>

            <!-- 4. Okos megoldások -->
            <div class="flex items-start gap-4">
              <svg xmlns="http://www.w3.org/2000/svg" width="64" height="65" viewBox="0 0 64 65" fill="none">
                <path
                  d="M32 55.5C34.2091 55.5 36 53.7091 36 51.5C36 49.2909 34.2091 47.5 32 47.5C29.7909 47.5 28 49.2909 28 51.5C28 53.7091 29.7909 55.5 32 55.5Z"
                  fill="#343330" />
                <path
                  d="M58 23.7975C50.6691 17.7851 41.4811 14.4993 32 14.4993C22.5189 14.4993 13.3309 17.7851 6 23.7975"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path
                  d="M50 32.7499C44.8768 28.6942 38.5342 26.4875 32 26.4875C25.4658 26.4875 19.1232 28.6942 14 32.7499"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
                <path
                  d="M42 41.7501C39.0942 39.6364 35.5933 38.4978 32 38.4978C28.4067 38.4978 24.9058 39.6364 22 41.7501"
                  stroke="#343330"
                  stroke-width="3"
                  stroke-linecap="round"
                  stroke-linejoin="round" />
              </svg>
              <div>
                <h3 style="color: var(--Dark, #242424)" class="font-['Red_Hat_Display'] font-[600] text-[30px] lg:text-[30px]">Okos megoldások</h3>
                <p style="color: var(--Dark, #242424)" class="mt-2  font-[600] text-[16px] font-['Red_Hat_Display']">
                  Wi‑Fi vezérlés, távoli hozzáférés és okoseszköz‑integráció a maximális kényelemért.
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- JOBB: piros CTA kártya -->
        <aside class="rounded-[28px] bg-[#F43F3F] text-white p-7 sm:p-10 shadow-[0_8px_28px_rgba(0,0,0,0.12)]">
          <h3 class="font-['Red_Hat_Display'] font-[700] text-[30px] lg:text-[35px]">
            Kérjen egyedi<br />
            árajánlatot
          </h3>
          <p class="mt-5 font-['Red_Hat_Display'] text-[16px]">
            Kérjen személyre szabott árajánlatot szakértő kollégáinktól, akik segítenek megtalálni az Ön számára legjobb megoldást. <br> <br> <strong>Gyors válasz, pontos
              tervezés, rejtett költségek nélkül.</strong> 
          </p>

          <NuxtLink style="color: var(--Dark, #242424)"
            to="/"
            class="mt-7 inline-flex w-full items-center justify-center rounded-[16px] bg-white px-8 py-5 text-lg font-semibold text-gray-900 hover:bg-white/95 transition font-['Red_Hat_Display'] text-[20px]  font-[700]">
            Árajánlat kérése
          </NuxtLink>
        </aside>
      </div>
    </div>
  </section>
</template>
