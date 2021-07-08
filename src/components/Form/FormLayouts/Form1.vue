<template>
  <div class="container mx-auto flex flex-wrap pt-3">
    <TextInput
      v-for="input in inputs"
      @update-text="updateFormData"
      :key="input.id"
      :input_purpose="input.input_purpose"
      :id="input.id"
      :placeholder="input.placeholder"
      :full_width="input.full_width"
      :leading_icon="input.leading_icon"
      :trailing_icon="input.trailing_icon"
      :icon="input.icon"
      :validation_failed="input.validation_failed"
    />
    <SelectDropdown
      v-for="dropdown in dropdowns"
      :key="dropdown.id"
      :id="dropdown.id"
      :input_purpose="dropdown.input_purpose"
      :options="dropdown.options"
      @update-select="updateFormData"
    />
    <Button
      :text="'Submit'"
      :larger="true"
      @button-click="submitForm"
    />
  </div>
</template>

<script>
  import TextInput from '../FormInputs/TextInput'
  import SelectDropdown from '../FormInputs/SelectDropdown'
  import Button from '../FormInputs/Button'
  import { ExclamationCircleIcon, QuestionMarkCircleIcon, MailIcon } from '@heroicons/vue/solid'

  export default {
    components: {
      TextInput,
      SelectDropdown,
      Button
    },

    data () {
      return {
        inputs: [
          { input_purpose: 'First Name', id: 'firstName', placeholder: 'Postman'},
          { input_purpose: 'Last Name', id: 'lastName', placeholder: 'Pat'},
          { input_purpose: 'Email', id: 'email', placeholder: 'postman.pat@thepost.com'},
          { input_purpose: 'Phone Number', id: 'phoneNumber', placeholder: '07770 70 70 70'},
          { input_purpose: 'House Number', id: 'houseNumber', placeholder: '1'},
          { input_purpose: 'Postcode', id: 'postcode', placeholder: 'CA20 1EU'},
          { input_purpose: 'Address', id: 'address', placeholder: 'Forge Cottage, Greendale, Cumbria', full_width: true},
          { input_purpose: 'Leading Icon Demo', id: 'leadingIcon', placeholder: 'black@ndwhite.cat', leading_icon: true, icon: MailIcon},
          { input_purpose: 'Trailing Icon Demo', id: 'trailingIcon', placeholder: 'What I make write in box?', trailing_icon: true, icon: QuestionMarkCircleIcon},
          { input_purpose: 'Validation FAILED', id: 'validationFailed', placeholder: 'foolish nonsense', trailing_icon: true, validation_failed: true, icon: ExclamationCircleIcon}
        ],
        dropdowns: [
          {
            input_purpose: 'Wall Surface',
            id: 'wallSurface',
            options: ['wood', 'concrete', 'brick', 'cardboard', 'waffles']
          }
        ],
        formData: {}
      }
    },

    methods: {
      updateFormData (payload) {
        const id = payload[0]
        const text = payload[1]
        this.formData[id] = text
      },
      submitForm () {
        console.log(this.formData)
      }
    }
  }
</script>
