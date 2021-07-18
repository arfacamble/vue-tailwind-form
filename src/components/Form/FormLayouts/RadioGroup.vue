<template>
  <div class="mt-5">
    <h2 class="pl-4 md:pl-8">{{question}}</h2>
    <div class="flex flex-wrap justify-evenly">
      <RadioOption
        v-for="option in options"
        :key="option.id"
        :id="option.id"
        :label="option.label"
        :icon="option.icon"
        :active="option.active"
        @set-active="setActive"
      />
      <div class="w-5/6 md:w-3/5">
        <TextInput
          v-if="requireMoreInfo"
          @update-text="updateMoreInfo"
          :input_purpose="more_info_input_purpose"
          :id="more_info_id"
          :placeholder="more_info_placeholder"
        />
      </div>
    </div>
  </div>
</template>

<script>
import RadioOption from '../FormInputs/RadioOption'
import TextInput from '../FormInputs/TextInput'

export default {
  components: {
    RadioOption,
    TextInput
  },

  props: {
    question: { required: true, type: String },
    options: { required: true, type: Object },
    id: { required: true, type: String },
    more_info_input_purpose: { type: String },
    more_info_id: { type: String },
    more_info_placeholder: { default: 'Tell us more', type: String }
  },

  methods: {
    setActive (optionId) {
      this.$emit('set-active', { inputId: this.id, active: optionId })
    },

    updateMoreInfo (payload) {
      this.$emit('update-more-info', { inputId: this.id, value: payload.value })
    }
  },

  computed: {
    requireMoreInfo () {
      const activeTab = Object.keys(this.options).find(id => this.options[id].active)
      if (activeTab) {
        return this.options[activeTab].require_more_info
      } else {
        return false
      }
    }
  }
}
</script>
