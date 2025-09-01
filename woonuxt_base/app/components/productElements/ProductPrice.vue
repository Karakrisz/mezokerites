<script setup lang="ts">
interface ProductPriceProps {
  regularPrice?: string | null;
  salePrice?: string | null;
}

const { regularPrice, salePrice } = defineProps<ProductPriceProps>();

// Ellenőrizzük, hogy van-e akciós ár és különbözik-e a rendes ártól
const hasValidSalePrice = computed(() => {
  return salePrice && salePrice !== regularPrice && salePrice.trim() !== '';
});

// A megjelenítendő ár
const displayPrice = computed(() => {
  return hasValidSalePrice.value ? salePrice : regularPrice;
});
</script>

<template>
  <div class="flex gap-[15px] items-center">
    <!-- Csak akkor jelenjen meg áthúzva a regular price, ha van érvényes sale price -->
    <span 
      v-if="hasValidSalePrice"
      class="line-through text-gray-500 text-[14px] uppercase" 
      v-html="regularPrice"
    />
    
    <!-- Az aktuális ár (sale price ha van, különben regular price) -->
    <span 
      class="text-[20px] uppercase font-bold"
      :class="hasValidSalePrice ? 'text-red-600' : 'text-gray-900'"
      v-html="displayPrice"
    />
  </div>
</template>