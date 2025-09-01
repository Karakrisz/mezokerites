<template>
  <form class="bg-white rounded-lg shadow" style="font-family: 'Red Hat Display';" @submit.prevent="saveChanges">
    <div class="grid p-8 gap-6 md:grid-cols-2">
      <h3 class="font-semibold text-xl col-span-full" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.billing') }}</h3>

      <div class="w-full">
        <label for="billing-first-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.firstName') }}</label>
        <input id="billing-first-name" v-model="customer.billing.firstName" placeholder="John" autocomplete="given-name" type="text" required style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-last-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.lastName') }}</label>
        <input id="billing-last-name" v-model="customer.billing.lastName" placeholder="Doe" autocomplete="family-name" type="text" required style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-phone" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.phone') }}</label>
        <input id="billing-phone" v-model="customer.billing.phone" placeholder="+1 234 567 8901" autocomplete="tel" type="tel" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-company" style="font-family: 'Red Hat Display';">Company ({{ $t('messages.general.optional') }})</label>
        <input id="billing-company" v-model="customer.billing.company" placeholder="Company Name" autocomplete="organization" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-address" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.address1') }}</label>
        <input id="billing-address" v-model="customer.billing.address1" placeholder="123 Main St" autocomplete="address-line1" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-address-2" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.address2') }} ({{ $t('messages.general.optional') }})</label>
        <input id="billing-address-2" v-model="customer.billing.address2" placeholder="Apartment, studio, or floor" autocomplete="address-line2" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-city" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.city') }}</label>
        <input id="billing-city" v-model="customer.billing.city" placeholder="New York" autocomplete="address-level2" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="billing-state" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.state') }} ({{ $t('messages.general.optional') }})</label>
        <StateSelect id="billing-state" v-model="customer.billing.state" :default-value="customer.billing.state" :country-code="customer.billing.country" />
      </div>

      <div class="w-full">
        <label for="billing-country" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.country') }}</label>
        <CountrySelect id="billing-country" v-model="customer.billing.country" :default-value="customer.billing.country" />
      </div>

      <div class="w-full">
        <label for="billing-zip" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.zip') }}</label>
        <input id="billing-zip" v-model="customer.billing.postcode" placeholder="10001" autocomplete="postal-code" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full col-span-full">
        <label for="billing-email" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.email') }}</label>
        <input id="billing-email" v-model="customer.billing.email" placeholder="johndoe@email.com" autocomplete="email" type="email" required style="font-family: 'Red Hat Display';">
      </div>
    </div>

    <div class="grid p-8 gap-6 md:grid-cols-2">
      <h3 class="font-semibold text-xl col-span-full" style="font-family: 'Red Hat Display';">{{ $t('messages.general.shipping') }}</h3>

      <div class="w-full">
        <label for="shipping-first-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.firstName') }}</label>
        <input id="shipping-first-name" v-model="customer.shipping.firstName" placeholder="John" autocomplete="given-name" type="text" required style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-last-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.lastName') }}</label>
        <input id="shipping-last-name" v-model="customer.shipping.lastName" placeholder="Doe" autocomplete="family-name" type="text" required style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-phone" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.phone') }}</label>
        <input id="shipping-phone" v-model="customer.shipping.phone" placeholder="+1 234 567 8901" autocomplete="tel" type="tel" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-company" style="font-family: 'Red Hat Display';">Company ({{ $t('messages.general.optional') }})</label>
        <input id="shipping-company" v-model="customer.shipping.company" placeholder="Company Name" autocomplete="organization" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-address" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.address1') }}</label>
        <input id="shipping-address" v-model="customer.shipping.address1" placeholder="O'Connell Street 47" autocomplete="address-line1" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-address-2" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.address2') }} ({{ $t('messages.general.optional') }})</label>
        <input
          id="shipping-address-2"
          v-model="customer.shipping.address2"
          placeholder="Apartment, studio, or floor"
          autocomplete="address-line2"
          type="text"
          style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-city" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.city') }}</label>
        <input id="shipping-city" v-model="customer.shipping.city" placeholder="New York" autocomplete="address-level2" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="shipping-state" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.state') }} ({{ $t('messages.general.optional') }})</label>
        <StateSelect id="shipping-state" v-model="customer.shipping.state" :default-value="customer.shipping.state" :country-code="customer.shipping.country" />
      </div>

      <div class="w-full">
        <label for="shipping-country" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.country') }}</label>
        <CountrySelect id="shipping-country" v-model="customer.shipping.country" :default-value="customer.shipping?.country" />
      </div>

      <div class="w-full">
        <label for="shipping-zip" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.zip') }}</label>
        <input id="shipping-zip" v-model="customer.shipping.postcode" placeholder="10001" autocomplete="postal-code" type="text" style="font-family: 'Red Hat Display';">
      </div>
    </div>

    <div class="bg-white backdrop-blur-sm bg-opacity-75 border-t col-span-full p-4 sticky bottom-0 rounded-b-lg">
      <button
        class="ml-auto flex items-center justify-center gap-3 px-6 py-3 text-white transition-colors"
        style="border-radius: 12px; background: var(--Secondary, #FD2D2D); font-family: 'Red Hat Display';"
        :disabled="loading">
        <LoadingIcon v-if="loading" color="#fff" size="20" />
        <span>{{ button.text }}</span>
      </button>
    </div>
  </form>
</template>

<script setup lang="ts">
const { viewer, customer } = useAuth();
const { t } = useI18n();

const loading = ref<boolean>(false);
const button = ref<{ text: string; color: string }>({ 
  text: t('messages.account.updateDetails'), 
  color: 'bg-primary hover:bg-primary-dark' 
});

async function saveChanges(): Promise<void> {
  loading.value = true;
  button.value.text = t('messages.account.updating');
  const shipping = customer.value.shipping;
  const billing = customer.value.billing;

  try {
    const { updateCustomer } = await GqlUpdateCustomer({ input: { id: viewer.value.id, shipping, billing } });
    if (updateCustomer) button.value = { text: t('messages.account.updateSuccess'), color: 'bg-green-500' };
  } catch (error) {
    button.value = { text: t('messages.account.failed'), color: 'bg-red-500' };
  }

  loading.value = false;

  setTimeout(() => {
    button.value = { text: t('messages.account.updateDetails'), color: 'bg-primary hover:bg-primary-dark' };
  }, 2000);
}
</script>