<template>
  <footer class="bg-[#4A8FF6] text-white py-10 font-montserrat">
    <div class="container mx-auto grid grid-cols-1 md:grid-cols-4 gap-8">
      
      <!-- Logo -->
      <div class="flex flex-col gap-4">
        <img src="/img/footer-logo.svg" alt="SioDoor" class="w-40" />
      </div>

      <!-- Menü -->
      <div>
        <h3 class="font-bold mb-4">MENÜ</h3>
        <ul class="space-y-2">
          <li><NuxtLink to="/">Rólunk</NuxtLink></li>
          <li><NuxtLink to="/">Garancia</NuxtLink></li>
          <li><NuxtLink to="/">Elállási jog</NuxtLink></li>
          <li><NuxtLink to="/">GDPR</NuxtLink></li>
          <li><NuxtLink to="/">Akciós termékeink</NuxtLink></li>
          <li><NuxtLink to="/">Képes vásárlói tájékoztató</NuxtLink></li>
        </ul>
      </div>

      <!-- Információk -->
      <div>
        <h3 class="font-bold mb-4">INFORMÁCIÓK</h3>
        <ul class="space-y-2 mb-6">
          <li><NuxtLink to="/cookie">Cookie tájékoztató</NuxtLink></li>
          <li><NuxtLink to="/adatkezelesi-tajekoztato">Adatkezelési tájékoztató</NuxtLink></li>
          <li><NuxtLink to="/aszf">ÁSZF</NuxtLink></li>
          <li><NuxtLink to="/gyik">Gyakran ismételt kérdések</NuxtLink></li>
          <li><NuxtLink to="/cegadatok">Cég adatok, elérhetőségek</NuxtLink></li>
          <li><NuxtLink to="/visszavetel">Visszavételi és jótállási feltételek</NuxtLink></li>
        </ul>
        <a href="https://digitalseed.hu/" target="_blank">
          <img src="/img/digitalseed.svg" alt="Digital Seed Studio" class="h-6" />
        </a>
      </div>

      <!-- Segítség -->
      <div>
        <h3 class="font-bold mb-4">SEGÍTSÉG</h3>
        <p class="mb-4">
          <strong>Nem tudja megrendelni termékét webshopunkban?</strong><br />
          Semmi gond! Írja meg nekünk a 
          <a href="mailto:megrendeles@siodoor.hu" class="underline">megrendeles@siodoor.hu</a> e-mail-címre, és kollégánk segít Önnek a rendelés felvételében.
        </p>
        <p class="mb-4">
          <strong>Kérdése van a termékeinkkel kapcsolatban?</strong><br />
          Írjon nekünk az 
          <a href="mailto:info@siodoor.hu" class="underline">info@siodoor.hu</a> címre, és készséggel válaszolunk.
        </p>
        <p>
          <strong>Elakadt a programozással?</strong><br />
          Hívjon: <a href="tel:+36305855620" class="underline">+36 30 585 5620</a>
        </p>
      </div>
    </div>
  </footer>
</template>