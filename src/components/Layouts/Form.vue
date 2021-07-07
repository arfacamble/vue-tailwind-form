<template>
  <div class="flex h-screen">
    <FormNav @select-tab="selectTab" />
    <Form1
      v-if="selectedTab === 'projects'"
    />
    <Form2
      v-if="selectedTab === 'grantInformation'"
    />
  </div>
</template>

<script>
  import FormNav from '../Form/FormLayouts/FormNav';
  import Form1 from '../Form/FormLayouts/Form1';
  import Form2 from '../Form/FormLayouts/Form2';

  export default {
    components: {
      FormNav,
      Form1,
      Form2
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
