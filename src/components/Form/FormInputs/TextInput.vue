<template>
  <div class="w-full">
    <label :for="input_purpose" :class="labelClass">{{input_purpose}}</label>
    <div :class="label_display ? 'mt-1 relative rounded-md shadow-sm' : ''">
      <div
        v-if="leading_icon"
        class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
      >
        <component
         :is="icon"
         class="h-5 w-5 text-gray-400"
         aria-hidden="true"
        />
      </div>
      <input
        type="text"
        v-model="text"
        @keyup="updateFormData"
        :name="input_purpose"
        :class="inputClass"
        :placeholder="placeholder"
      />
      <div
        v-if="trailing_icon"
        class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
      >
        <component
          :is="icon"
          :class="[validation_failed ? 'text-red-500' : 'text-gray-400', 'h-5 w-5']"
          aria-hidden="true"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    input_purpose: {
      required: true,
      type: String
    },
    id: {
      required: true,
      type: String
    },
    placeholder: {
      required: true,
      type: String
    },
    label_display: {
      default: true,
      type: Boolean
    },
    full_width: { /* for address field, stays full width on big screen */
      default: false,
      type: Boolean
    },
    leading_icon: {
      default: false,
      type: Boolean
    },
    trailing_icon: {
      default: false,
      type: Boolean
    },
    validation_failed: {
      default: false,
      type: Boolean
    },
    icon: {
      type: undefined
    }
    // another prop for color given focus classes?
    // or hardcoded our own color as consistent across app?
  },

  computed: {
    labelClass () {
      return (this.label_display ? "block text-sm font-medium text-gray-700" : "sr-only")
    },
    inputClass () {
      let inputClass = 'block w-full p-2 sm:text-sm rounded-md'
      if (this.leading_icon) {
        inputClass += ' pl-10'
      }
      if (this.trailing_icon) {
        inputClass += ' pr-10'
      }
      if (this.validation_failed) {
        inputClass += ' border border-red-300 text-red-900 placeholder-red-300 focus:outline-none focus:ring-red-500 focus:border-red-500'
      } else {
        inputClass += ' shadow-sm focus:ring-indigo-500 focus:border-indigo-500 border-gray-300'
      }
      return inputClass
    }
  },

  data () {
    return {
      text: ''
    }
  },

  methods: {
    updateFormData () {
      this.$emit('update-text', { inputId: this.id, value: this.text })
    }
  }
}
</script>
