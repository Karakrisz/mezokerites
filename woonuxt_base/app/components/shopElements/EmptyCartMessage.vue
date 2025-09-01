<script setup lang="ts">
const { toggleCart } = useCart();
</script>

<template>
  <div class="flex flex-col items-center justify-center flex-1 mb-20">
    <Icon name="ion:cart-outline text-gray-400" size="96" class="opacity-75 mb-5" />
    <div class="mb-2 text-xl font-semibold text-gray-600" style="font-family: 'Red Hat Display';">
      {{ $t('messages.shop.cartEmpty') }}
    </div>
    <span class="mb-8" style="font-family: 'Red Hat Display';">
      {{ $t('messages.shop.addProductsInYourCart') }}
    </span>
    <NuxtLink
      to="/products"
      class="inline-flex items-center justify-center px-6 py-3 text-white transition-colors"
      style="border-radius: 12px; background: var(--Primary, #4285F4); font-family: 'Red Hat Display';"
      @click="toggleCart(false)">
      {{ $t('messages.shop.browseOurProducts') }}
    </NuxtLink>
  </div>
</template>