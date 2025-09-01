<script setup>
import { ref, watch } from 'vue'

const { getSearchQuery, setSearchQuery, clearSearchQuery } = useSearching()
const searchQuery = ref(getSearchQuery())

const reset = () => {
  clearSearchQuery()
  searchQuery.value = ''
}

watch(getSearchQuery, (value) => {
  if (!value) reset()
})

const handleSubmit = () => {
  setSearchQuery(searchQuery.value)
}
</script>

<template>
  <form class="relative w-full max-w-md mr-10" @submit.prevent="handleSubmit">
    <!-- Input mező -->
    <input
      v-model="searchQuery"
      type="text"
      placeholder="Keresés"
      class="w-full ml-10 pr-12 text-lg text-gray-900 bg-transparent border-0 border-b-2 border-gray-900 outline-none focus:border-gray-900 placeholder:text-gray-500 font-['Red_Hat_Display'] font-[600] text-[16px]"
    >
    
    <!-- X gomb törléshez -->
    <button
      v-if="searchQuery"
      type="button"
      @click="reset"
      class="absolute right-10 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600 transition-colors"
    >
      <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
        <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
      </svg>
    </button>

    <!-- Keresés gomb -->
    <button
      type="submit"
      class="absolute right-0 top-1/2 -translate-y-1/2 p-1 text-gray-900 hover:text-gray-600 transition-colors"
    >
      <img src="/img/search.svg" alt="Keresés" class="w-6 h-6" />
    </button>
  </form>
</template>

<style scoped>
/* Eltávolítjuk a böngésző alapértelmezett input stílusait */
input:focus {
  outline: none;
  box-shadow: none;
}

/* Smooth transition a border színhez */
input {
  transition: border-color 0.2s ease;
}
</style>