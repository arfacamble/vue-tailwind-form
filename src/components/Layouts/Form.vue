<template>
  <div class="h-screen">
    <div
      class="md:sr-only h-20 flex justify-center"
      style="background-image: url('../../assets/electron-logo-flat.jpeg')"
    >
      <img
        src="../../assets/electron-logo-flat.jpeg"
        alt="electron logo"
      >
    </div>
    <div class="flex h-screen p-2 pt-0 md:pt-2">
      <div class="h-screen">
        <img
          class="sr-only md:not-sr-only md:w-56"
          src="../../assets/electron-logo-light.png"
          alt="electron logo"
        >
        <!-- <FormNav @select-tab="selectTab" /> -->
        <FormNav2 @select-tab="selectTab" />
      </div>
      <div class="h-screen w-full">
        <Form1
          v-if="selectedTab === 'projects'"
        />
        <Form2
          v-if="selectedTab === 'grantInformation'"
        />
        <Form3
          v-if="selectedTab === 'installationDetails'"
        />
      </div>
    </div>
  </div>
</template>

<script>
  // import FormNav from '../Form/FormLayouts/FormNav';
  import FormNav2 from '../Form/FormLayouts/FormNav2';
  import Form1 from '../Form/FormLayouts/Form1';
  import Form2 from '../Form/FormLayouts/Form2';
  import Form3 from '../Form/FormLayouts/Form3';

  export default {
    components: {
      // FormNav,
      FormNav2,
      Form1,
      Form2,
      Form3,
    },

    methods: {
      selectTab (event) {
        this.selectedTab = event.id
      }
    },

    data () {
      return {
        selectedTab: 'projects'
      }
    }
  }
</script>
