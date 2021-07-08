<template>
  <div class="container mx-auto flex flex-wrap pt-3">
    <TextInput
      v-for="input in inputs"
      :key="input.id"
      :input_purpose="input.name"
      :id="input.id"
      :placeholder="input.placeholder"
    />
    <TextInput
      v-for="input in full_width_inputs"
      :key="input.id"
      :input_purpose="input.name"
      :id="input.id"
      :placeholder="input.placeholder"
      :full_width="true"
    />
    <TextInput
      :input_purpose="'leading icon demo'"
      :placeholder="'black@ndwhite.cat'"
      :leading_icon="true"
      :id="'leading-icon'"
    >
      <MailIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
    </TextInput>
    <TextInput
      :input_purpose="'trailing icon demo'"
      :placeholder="'What I make write in box?'"
      :trailing_icon="true"
      :id="'trailing-icon'"
    >
      <QuestionMarkCircleIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
    </TextInput>
    <SelectDropdown
      :input_purpose="'Wall Surface'"
      :options="dropdownOptions"
    />
    <TextInput
      :input_purpose="'validation FAILED'"
      :placeholder="'foolish rubbish'"
      :trailing_icon="true"
      :validation_failed="true"
      :id="'red-red-red'"
    >
      <ExclamationCircleIcon class="h-5 w-5 text-red-500" aria-hidden="true" />
    </TextInput>
  </div>
</template>

<script>
  import TextInput from '../FormInputs/TextInput'
  import SelectDropdown from '../FormInputs/SelectDropdown'
  import { ExclamationCircleIcon, QuestionMarkCircleIcon, MailIcon } from '@heroicons/vue/solid'

  export default {
    components: {
      TextInput,
      SelectDropdown,
      ExclamationCircleIcon,
      MailIcon,
      QuestionMarkCircleIcon
    },

    data () {
      return {
        inputs: [
          { name: 'First Name', id: 'firstName', placeholder: 'Postman'},
          { name: 'Last Name', id: 'lastName', placeholder: 'Pat'},
          { name: 'Email', id: 'email', placeholder: 'postman.pat@thepost.com'},
          { name: 'Phone Number', id: 'phoneNumber', placeholder: '07770 70 70 70'},
          { name: 'House Number', id: 'houseNumber', placeholder: '1'},
          { name: 'First Name', id: 'postcode', placeholder: 'CA20 1EU'}
        ],
        full_width_inputs: [
          { name: 'Address', id: 'address', placeholder: 'Forge Cottage, Greendale, Cumbria'}
        ],
        dropdownOptions: [
          'wood', 'concrete', 'brick', 'cardboard', 'waffles'
        ]
      }
    }
  }
</script>
