<template>
  <div class="my-5">
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
    </div>
  </div>
</template>

<script>
import RadioOption from '../FormInputs/RadioOption'

export default {
  components: {
    RadioOption
  },

  props: {
    question: {
      required: true,
      type: String
    },
    options: {
      required: true,
      type: Object
    },
    id: {
      required: true,
      type: String
    }
  },

  methods: {
    setActive (optionId) {
      this.$emit('set-active', { inputId: this.id, active: optionId })
    }
  }
}
</script>
