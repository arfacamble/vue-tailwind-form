<template>
  <div class="flex flex-wrap">
    <div
      v-for="question in questions"
      :key="question.id"
      :class="['w-full mx-auto p-4', question.half_width ? ' md:w-2/4' : '']"
    >
      <div v-if="question.component === 'textInput'">
        <TextInput
          :input_purpose="question.input_purpose"
          :placeholder="question.placeholder"
          :label_display="question.label_display"
          :id="question.id"
          @update-text="updateFormData"
        />
      </div>
      <div v-if="question.component === 'radioGroup'">
        <RadioGroup
          :question="question.question"
          :id="question.id"
          :options="question.options"
          @set-active="setRadioActive"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import TextInput from '../FormInputs/TextInput'
  import RadioGroup from './RadioGroup'

  export default {
    components: {
      TextInput,
      RadioGroup
    },

    props: {
      formId: {
        required: true,
        type: String
      },
      questions: {
        required: true,
        type: Object
      }
    },

    methods: {
      updateFormData (payload) {
        this.$emit('update-form-data', { formId: this.formId, inputId: payload.inputId, value: payload.value })
      },
      setRadioActive (payload) {
        this.$emit('update-radio-active', { formId: this.formId, inputId: payload.inputId, setActive: payload.active })
      }
    }
  }
</script>
