<template>
  <form v-if="customer" class="bg-white rounded-lg shadow" style="font-family: 'Red Hat Display';" @submit.prevent="saveChanges">
    <div class="grid gap-6 p-8 md:grid-cols-2">
      <h3 class="text-xl font-semibold col-span-full" style="font-family: 'Red Hat Display';">{{ $t('messages.account.personalInfo') }}</h3>

      <div class="w-full">
        <label for="first-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.firstName') }}</label>
        <input id="first-name" v-model="customer.firstName" placeholder="John" autocomplete="given-name" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="last-name" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.lastName') }}</label>
        <input id="last-name" v-model="customer.lastName" placeholder="Doe" autocomplete="family-name" type="text" style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="username" style="font-family: 'Red Hat Display';">{{ $t('messages.account.username') }} ({{ $t('messages.general.readOnly') }})</label>
        <input id="username" v-model="customer.username" placeholder="johndoe" autocomplete="username" type="text" readonly style="font-family: 'Red Hat Display';">
      </div>

      <div class="w-full">
        <label for="email" style="font-family: 'Red Hat Display';">{{ $t('messages.billing.email') }}</label>
        <input id="email" v-model="customer.email" placeholder="johndoe@email.com" autocomplete="email" type="email" style="font-family: 'Red Hat Display';">
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

async function saveChanges() {
  if (!viewer.value) {
    console.error('No viewer available');
    return;
  }

  loading.value = true;
  button.value.text = t('messages.account.updating');
  const firstName = customer.value.firstName;
  const lastName = customer.value.lastName;
  try {
    const { updateCustomer } = await GqlUpdateCustomer({ input: { id: viewer.value.id, firstName, lastName } });
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