<template>
  <div class="h-screen">
    <div class="md:sr-only h-20 flex justify-center" >
      <img
        src="../../assets/electron-logo-flat.jpeg"
        alt="electron logo"
      >
    </div>
    <div class="flex h-5/6 md:h-screen p-2 pt-0 md:pt-2">
      <div class="h-full">
        <img
          class="sr-only md:not-sr-only md:w-56"
          src="../../assets/electron-logo-light.png"
          alt="electron logo"
        >
        <FormNav2
          :tabs="tabs"
          @select-tab="selectTab"
        />
      </div>
      <div class="h-full w-full">
        <FormYourDetails v-if="selectedTab === 'yourDetails'" />
        <Form2 v-if="selectedTab === 'grantInformation'" />
        <Form3 v-if="selectedTab === 'propertyDetails'" />
        <Form4 v-if="selectedTab === 'chargerAndAccessories'" />
        <Form5 v-if="selectedTab === 'payment'" />
      </div>
    </div>
  </div>
</template>

<script>
  import FormNav2 from '../Form/General/FormNav2';
  import FormYourDetails from '../Form/FormLayouts/FormYourDetails';
  import Form2 from '../Form/FormLayouts/Form2';
  import Form3 from '../Form/FormLayouts/Form3';
  import Form4 from '../Form/FormLayouts/Form4';
  import Form5 from '../Form/FormLayouts/Form5';

  export default {
    components: {
      FormNav2,
      FormYourDetails,
      Form2,
      Form3,
      Form4,
      Form5
    },

    data () {
      return {
        tabs: {
          yourDetails: { order: 1, id: 'yourDetails', title: 'Your Details', current: true, complete: false },
          grantInformation: { order: 2, id: 'grantInformation', title: 'Grant Information', current: false, complete: false },
          propertyDetails: { order: 3, id: 'propertyDetails', title: 'Property Details', current: false, complete: false },
          chargerAndAccessories: { order: 4, id: 'chargerAndAccessories', title: 'Charger & Accessories', current: false, complete: false },
          payment: { order: 5, id: 'payment', title: 'Payment', current: false, complete: false },
          booking: { order: 6, id: 'booking', title: 'Booking', current: false, complete: false }
        },
        selectedTab: 'yourDetails'
      }
    },

    methods: {
      selectTab (tabId) {
        this.tabs[this.selectedTab].current = false
        this.selectedTab = tabId
        this.tabs[this.selectedTab].current = true
      }
    }
  }
</script>
