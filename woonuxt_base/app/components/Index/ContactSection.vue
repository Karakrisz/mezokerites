<!-- components/SectionContact.vue -->
<script setup lang="ts">
import { reactive, ref } from 'vue';

const form = reactive({
  name: '',
  email: '',
  phone: '',
  message: '',
});
const submitting = ref(false);
const sent = ref(false);

const onSubmit = async () => {
  submitting.value = true;
  // TODO: küldés API-ra (pl. /api/contact) – ide jöhet a fetch()
  await new Promise((r) => setTimeout(r, 600)); // demo delay
  submitting.value = false;
  sent.value = true;
};
</script>

<template>
  <section class="py-16 sm:py-24">
    <div class="container mx-auto px-6 sm:px-12">
      <div class="grid overflow-hidden rounded-[24px] border-2 border-[#CCC] bg-white lg:grid-cols-2">
        <!-- Form -->
        <div class="p-6 sm:p-10 lg:p-14">
          <h2 class="text-4xl sm:text-5xl font-semibold text-gray-900 mb-8">Lépjünk kapcsolatba</h2>

          <form @submit.prevent="onSubmit" class="space-y-6 max-w-xl">
            <!-- Név -->
            <div>
              <label for="name" class="sr-only">Név</label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                required
                autocomplete="name"
                placeholder="Név*"
                class="w-full border-0 border-b border-gray-300 bg-transparent px-0 py-3 focus:border-gray-900 focus:ring-0" />
            </div>

            <!-- Email -->
            <div>
              <label for="email" class="sr-only">E‑mail cím</label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                required
                autocomplete="email"
                placeholder="E‑mail cím*"
                class="w-full border-0 border-b border-gray-300 bg-transparent px-0 py-3 focus:border-gray-900 focus:ring-0" />
            </div>

            <!-- Telefon -->
            <div>
              <label for="phone" class="sr-only">Telefonszám</label>
              <input
                id="phone"
                v-model="form.phone"
                type="tel"
                required
                inputmode="tel"
                autocomplete="tel"
                placeholder="Telefonszám*"
                class="w-full border-0 border-b border-gray-300 bg-transparent px-0 py-3 focus:border-gray-900 focus:ring-0" />
            </div>

            <!-- Megjegyzés -->
            <div>
              <label for="message" class="sr-only">Üzenet</label>
              <input
                id="message"
                v-model="form.message"
                type="text"
                placeholder="Üzenet"
                class="w-full border-0 border-b border-gray-300 bg-transparent px-0 py-3 focus:border-gray-900 focus:ring-0" />
            </div>

            <button
              type="submit"
              :disabled="submitting"
              class="inline-flex items-center justify-center rounded-[12px] bg-[#242424] px-[40px] py-[16px] text-white font-semibold disabled:opacity-60">
              Árajánlat kérése
            </button>

            <p v-if="sent" class="text-green-600">Köszönjük! Hamarosan jelentkezünk.</p>
          </form>
        </div>

        <!-- Kép -->
        <div class="relative min-h-[280px]">
          <img src="/img/contact.webp" alt="Kapubejáró esti fényekkel" class="absolute inset-0 h-full w-full object-cover" loading="lazy" decoding="async" />
        </div>
      </div>
    </div>
  </section>
</template>