<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const track = ref<HTMLElement | null>(null);
let isDown = false;
let startX = 0;
let startScroll = 0;
let autoScrollInterval: ReturnType<typeof setInterval> | null = null;
let userInteracted = false;
let resumeTimeout: ReturnType<typeof setTimeout> | null = null;
let currentPointerId: number | null = null;

const startAutoScroll = () => {
  stopAutoScroll();
  autoScrollInterval = setInterval(() => {
    if (!track.value || isDown) return;
    track.value.scrollLeft += 1;
    
    // Ha elértük a végét, visszaugrunk az elejére
    if (track.value.scrollLeft >= track.value.scrollWidth - track.value.clientWidth) {
      track.value.scrollLeft = 0;
    }
  }, 20);
};

const stopAutoScroll = () => {
  if (autoScrollInterval) {
    clearInterval(autoScrollInterval);
    autoScrollInterval = null;
  }
};

const delayAutoScrollResume = () => {
  stopAutoScroll();
  if (resumeTimeout) clearTimeout(resumeTimeout);
  
  resumeTimeout = setTimeout(() => {
    if (!isDown) { // Csak akkor indítsd újra, ha nincs aktív húzás
      startAutoScroll();
    }
  }, 3000);
};

const onDown = (e: PointerEvent) => {
  if (!track.value) return;
  
  e.preventDefault();
  isDown = true;
  userInteracted = true;
  currentPointerId = e.pointerId;
  
  track.value.setPointerCapture(e.pointerId);
  startX = e.clientX;
  startScroll = track.value.scrollLeft;
  stopAutoScroll();
  
  // Cursor változtatás
  track.value.style.cursor = 'grabbing';
};

const onMove = (e: PointerEvent) => {
  if (!isDown || !track.value || e.pointerId !== currentPointerId) return;
  
  e.preventDefault();
  const delta = e.clientX - startX;
  track.value.scrollLeft = startScroll - delta;
};

const onUp = (e: PointerEvent) => {
  if (!track.value || !isDown) return;
  
  isDown = false;
  
  // Pointer capture elengedése
  if (currentPointerId !== null) {
    try {
      track.value.releasePointerCapture(currentPointerId);
    } catch (error) {
      // Némán elnyeljük a hibát
    }
    currentPointerId = null;
  }
  
  // Cursor visszaállítása
  track.value.style.cursor = 'grab';
  
  // Automatikus scroll újraindítása, ha a felhasználó interaktált
  if (userInteracted) {
    delayAutoScrollResume();
  }
};

// Scroll esemény kezelése (ha valaki scroll wheel-lel mozgatja)
const onScroll = () => {
  if (!isDown) {
    userInteracted = true;
    delayAutoScrollResume();
  }
};

onMounted(() => {
  // Kis késleltetéssel indítjuk el az automatikus scrollt
  setTimeout(() => {
    startAutoScroll();
  }, 1000);
  
  // Scroll event listener hozzáadása
  if (track.value) {
    track.value.addEventListener('scroll', onScroll, { passive: true });
  }
});

onUnmounted(() => {
  stopAutoScroll();
  if (resumeTimeout) {
    clearTimeout(resumeTimeout);
  }
  
  // Event listener eltávolítása
  if (track.value) {
    track.value.removeEventListener('scroll', onScroll);
  }
});
</script>

<template>
  <section class="py-16 sm:py-24">
    <div class="container mx-auto px-6 sm:px-12">
      <h2 class="text-4xl sm:text-5xl font-semibold text-gray-900 mb-8">Partnereink</h2>

      <div
        ref="track"
        class="partner-track relative flex gap-5 overflow-x-auto snap-x snap-mandatory scroll-smooth select-none py-2 cursor-grab touch-pan-x"
        @pointerdown="onDown"
        @pointermove="onMove"
        @pointerup="onUp"
        @pointerleave="onUp"
        @pointercancel="onUp"
        style="cursor: grab;">
        
        <!-- Partner elemek -->
        <div
          v-for="n in 8"
          :key="n"
          class="snap-start shrink-0 w-[180px] sm:w-[200px] h-[140px] sm:h-[150px] rounded-[24px] border border-[#CCC] bg-white flex items-center justify-center hover:shadow-md transition-shadow">
          <img 
            :src="n === 1 ? '/img/partner.png' : `/img/partner${n}.png`"
            :alt="`Partner ${n} logó`" 
            class="max-h-[70%] max-w-[70%] object-contain pointer-events-none" 
            loading="lazy" 
            decoding="async"
            draggable="false" />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.partner-track {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.partner-track::-webkit-scrollbar {
  display: none;
}

/* Touch készülékek támogatása */
.partner-track {
  touch-action: pan-x;
}
</style>