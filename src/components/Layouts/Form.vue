<template>
  <div class="flex h-screen">
    <FormNav @select-tab="selectTab" />
    <Form1 />
  </div>
</template>

<script>
  import FormNav from '../Form/FormLayouts/FormNav';
  import Form1 from '../Form/FormLayouts/Form1';
  export default {
    components: {
      FormNav,
      Form1
    },

    methods: {
      selectTab (event) {
        console.log(event)
      }
    }
  }
</script>
