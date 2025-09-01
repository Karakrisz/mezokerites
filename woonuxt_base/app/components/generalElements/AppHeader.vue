<script setup lang="ts">
const links = [
  { name: 'Termékek', link: '/', prefetch: true },
  { name: 'Garázskapu Tervező', link: '/' },
  { name: 'Viszonteladóknak', link: '/', prefetch: true },
];
</script>

<template>
  <header class="z-50 top-0 bg-white py-4">
    <div class="menu container flex justify-between items-center gap-10">
      <!-- Logo bal oldalt -->
      <NuxtLink to="/" class="shrink-0">
        <div class="flex items-center">
          <span class="font-bold text-[#FF5D19] pl-2">
            <NuxtImg src="/img/logo.webp" class="h-[55px]" />
          </span>
        </div>
      </NuxtLink>

      <!-- Menü és kosár jobb oldalt -->
      <div class="flex items-center gap-8">
        <!-- Mobile menu trigger -->
        <MenuTrigger class="lg:hidden" />
        
        <!-- Desktop navigáció -->
        <div class="space-x-20 lg:flex items-center hidden">
          <NuxtLink 
            v-for="link in links" 
            :key="link.name" 
            :to="link.link" 
            class="font-['Red_Hat_Display'] font-[600] text-[16px] hover:text-[#FD2D2D] transition-colors duration-200"
          >
            {{ link.name }}
          </NuxtLink>
        </div>

        <!-- Jobb oldali gombok -->
        <div class="flex gap-4">
          <ProductSearch class="hidden md:inline-flex max-w-[320px]" />
          <SignInLink />
          <!-- CartTrigger wrapper a narancssárga háttérhez -->
          <div class="rounded-md">
            <CartTrigger class="text-white" />
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped>
.menu {
}

:deep(.cart-trigger) {
  color: white;
  background: transparent;
}

:deep(.cart-trigger):hover {
  background: rgba(255, 255, 255, 0.1);
}
</style>