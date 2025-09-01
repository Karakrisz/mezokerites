<script setup lang="ts">
const { toggleMobileMenu } = useHelpers();

const links = [
  { text: "Termékek", to: "/", prefetch: false },
  { text: "Garázskapu Tervező", to: "/", prefetch: false },
  { text: "Viszonteladóknak", to: "/", prefetch: false },
];
</script>

<template>
  <div class="bg-white flex flex-col max-w-lg shadow-lg top-0 bottom-0 left-0 w-11/12 z-50 fixed overflow-x-hidden p-20" style="font-family: 'Red Hat Display';">
    <Icon 
      name="ion:close-outline" 
      class="absolute p-1 rounded-lg shadow-lg top-6 left-6 md:left-8 cursor-pointer transition" 
      style="color: var(--Secondary, #FD2D2D);" 
      size="34" 
      @click="toggleMobileMenu(false)" 
    />

    <div class="flex flex-col items-center justify-center h-full gap-10">
      <ProductSearch class="h-fit w-full relative" />
      <nav class="flex flex-col items-center justify-center gap-10">
        <NuxtLink
          v-for="link in links" 
          :key="link.to" 
          :to="link.to" 
          :class="[
            'cursor-pointer text-lg transition font-[600]',
            link.class
          ]" 
          style="font-family: 'Red Hat Display'; color: #242424;"
          :prefetch="link.prefetch"
          @mouseover="$event.target.style.color = 'var(--Secondary, #FD2D2D)'"
          @mouseleave="$event.target.style.color = '#242424'">
          {{ link.text }}
        </NuxtLink>
      </nav>
    </div>
  </div>
</template>