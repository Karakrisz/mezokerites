<script setup lang="ts">
const route = useRoute();
const { storeSettings } = useAppConfig();
const { addToCart, isUpdatingCart } = useCart();

const props = defineProps({
  node: { type: Object as PropType<Product>, required: true },
  index: { type: Number, default: 1 },
});

// Lokális loading állapot erre a termékre
const isAddingToCart = ref(false);
const isAddedToCart = ref(false);

// example: ?filter=pa_color[green,blue],pa_size[large]
const filterQuery = ref(route.query?.filter as string);
const paColor = ref(filterQuery.value?.split('pa_color[')[1]?.split(']')[0]?.split(',') || []);

// watch filterQuery
watch(
  () => route.query,
  () => {
    filterQuery.value = route.query.filter as string;
    paColor.value = filterQuery.value?.split('pa_color[')[1]?.split(']')[0]?.split(',') || [];
  },
);

const mainImage = computed<string>(() => props.node?.image?.producCardSourceUrl || props.node?.image?.sourceUrl || '/images/placeholder.jpg');
const imagetoDisplay = computed<string>(() => {
  if (paColor.value.length) {
    const activeColorImage = props.node?.variations?.nodes.filter((variation) => {
      const hasMatchingAttributes = variation.attributes?.nodes.some((attribute) => paColor.value.some((color) => attribute?.value?.includes(color)));
      const hasMatchingSlug = paColor.value.some((color) => variation.slug?.includes(color));
      return hasMatchingAttributes || hasMatchingSlug;
    });
    if (activeColorImage?.length) return activeColorImage[0]?.image?.producCardSourceUrl || activeColorImage[0]?.image?.sourceUrl || mainImage.value;
  }
  return mainImage.value;
});

// Biztonságos slug kezelés
const safeSlug = computed(() => props.node.slug || '');
const productUrl = computed(() => safeSlug.value ? `/product/${decodeURIComponent(safeSlug.value)}` : '#');

// Kosárba helyezés kezelése
const handleAddToCart = async () => {
  if (!props.node.databaseId || isAddingToCart.value) return;
  
  try {
    isAddingToCart.value = true;
    await addToCart({ productId: props.node.databaseId, quantity: 1 });
    
    // Siker esetén
    isAddedToCart.value = true;
    
    // Hang lejátszása
    playAddToCartSound();
    
    // 2 másodperc után visszaállítjuk az eredeti állapotot
    setTimeout(() => {
      isAddedToCart.value = false;
    }, 2000);
    
  } catch (error) {
    console.error('Hiba a kosárba helyezés során:', error);
  } finally {
    isAddingToCart.value = false;
  }
};

// Hang lejátszás
const playAddToCartSound = () => {
  try {
    // Egyszerű "ding" hang AudioContext-tel
    const audioContext = new (window.AudioContext || (window as any).webkitAudioContext)();
    const oscillator = audioContext.createOscillator();
    const gainNode = audioContext.createGain();
    
    oscillator.connect(gainNode);
    gainNode.connect(audioContext.destination);
    
    oscillator.frequency.setValueAtTime(800, audioContext.currentTime);
    oscillator.frequency.setValueAtTime(1000, audioContext.currentTime + 0.1);
    
    gainNode.gain.setValueAtTime(0, audioContext.currentTime);
    gainNode.gain.linearRampToValueAtTime(0.1, audioContext.currentTime + 0.01);
    gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
    
    oscillator.start(audioContext.currentTime);
    oscillator.stop(audioContext.currentTime + 0.3);
  } catch (error) {
    console.log('Hang lejátszás nem sikerült:', error);
  }
};
</script>

<template>
  <div class="product-card relative bg-white rounded-[24px] border border-[#CCC] overflow-hidden hover:shadow-lg transition-all duration-300 group">
    <!-- Sale Badge -->
    <SaleBadge :node class="absolute top-4 right-4 z-10" />

    <!-- Termék kép -->
    <div class="relative aspect-[4/3] bg-gray-50 overflow-hidden">
      <img 
        :src="imagetoDisplay" 
        :alt="node.name || 'Termék kép'"
        class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"
        loading="lazy"
      />
      
      <!-- Hover overlay - finom árnyékolás -->
      <div class="absolute inset-0 bg-black/5 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
    </div>

    <!-- Termék információk -->
    <div class="p-6 space-y-4">
      <!-- Termék név -->
      <h3 class="font-['Montserrat'] font-[600] text-[16px] leading-tight line-clamp-2 uppercase" style="color: #242424;">
        {{ node.name }}
      </h3>

      <!-- Termék leírás (opcionális - ha van rövid leírás) -->
      <div 
        v-if="node.shortDescription"
        class="text-gray-600 text-sm leading-relaxed line-clamp-2"
        v-html="node.shortDescription"
      />

      <!-- Ár -->
      <div class="py-2">
        <ProductPrice 
          class="font-['Montserrat'] text-xl font-bold" 
          style="color: #242424;"
          :sale-price="node.salePrice" 
          :regular-price="node.regularPrice" 
        />
      </div>

      <!-- Kosárba gomb -->
      <button 
        v-if="node.slug && node.databaseId"
        @click="handleAddToCart"
        :disabled="isAddingToCart"
        :class="[
          'w-full py-3 px-6 font-[600] text-[16px] rounded-[12px] transition-all duration-200 flex items-center justify-center gap-2',
          isAddedToCart 
            ? 'bg-green-500 text-white' 
            : 'bg-[#4285F4] hover:bg-[#3367D6] disabled:bg-gray-300 text-white'
        ]"
        style="font-family: 'Red Hat Display';"
      >
        <span v-if="isAddedToCart">Hozzáadva a kosárhoz</span>
        <span v-else-if="isAddingToCart">Hozzáadás...</span>
        <span v-else>Kosárba</span>
        
        <!-- Loading spinner -->
        <div v-if="isAddingToCart" class="w-4 h-4 border-2 border-white/30 border-t-white rounded-full animate-spin"></div>
        
        <!-- Checkmark ikon siker esetén -->
        <svg v-if="isAddedToCart" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
        </svg>
      </button>

      <!-- Megtekintés link -->
      <div class="text-center">
        <NuxtLink 
          :to="productUrl" 
          :title="node.name"
          class="font-['Red_Hat_Display'] font-[600] text-[16px] text-gray-600 hover:text-[#4285F4] transition-colors duration-200"
        >
          Megtekintés
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Line clamp utilities */
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* Product card hover effects */
.product-card:hover {
  box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

/* Custom scrollbar if needed */
.product-card::-webkit-scrollbar {
  display: none;
}

/* Ensure consistent height for cards in grid */
.product-card {
  height: 100%;
  display: flex;
  flex-direction: column;
}

.product-card > div:last-child {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>