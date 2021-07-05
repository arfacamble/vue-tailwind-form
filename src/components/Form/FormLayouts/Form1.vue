<template>
  <div class="h-screen w-full">
    <div class="container mx-auto flex flex-wrap">
      <TextInput
        v-for="input in inputs"
        :key="input.id"
        :input_purpose="input.name"
        :id="input.id"
        :label_display="true"
        :placeholder="input.placeholder"
      />
    </div>
  </div>
</template>

<script>
  import TextInput from '../FormInputs/TextInput'

  export default {
    components: {
      TextInput
    },

    data () {
      return {
        inputs: [
          { name: 'First Name', id: 'firstName', placeholder: 'Postman', label: true},
          { name: 'Last Name', id: 'lastName', placeholder: 'Pat', label: true},
          { name: 'Email', id: 'email', placeholder: 'postman.pat@thepost.com', label: true},
          { name: 'Phone Number', id: 'phoneNumber', placeholder: '07770 70 70 70', label: true},
          { name: 'House Number', id: 'houseNumber', placeholder: '1', label: true},
          { name: 'First Name', id: 'postcode', placeholder: 'CA20 1EU', label: true},
          { name: 'First Name', id: 'address', placeholder: 'Forge Cottage, Greendale, Cumbria', label: true}
        ]
      }
    }
  }
</script>
