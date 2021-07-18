<template>
  <div class="flex flex-wrap">
    <div
      v-for="question in questions"
      :key="question.id"
      :class="['w-full mx-auto px-4 pt-4', question.half_width ? ' md:w-2/4' : '']"
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
          :more_info_input_purpose="question.more_info_input_purpose"
          :more_info_id="question.more_info_id"
          :more_info_placeholder="question.more_info_placeholder"
          @set-active="setRadioActive"
          @update-more-info="updateRadioMoreInfo"
        />
      </div>
      <div v-if="question.component === 'dragAndDrop'">
        <DragAndDrop
          :hint="question.hint"
          :id="question.id"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import TextInput from '../FormInputs/TextInput'
  import DragAndDrop from '../FormInputs/DragAndDrop'
  import RadioGroup from './RadioGroup'

  export default {
    components: {
      TextInput,
      RadioGroup,
      DragAndDrop
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
      },
      updateRadioMoreInfo (payload) {
        this.$emit('update-radio-more-info', { formId: this.formId, inputId: payload.inputId, value: payload.value })
      }
    }
  }
</script>
