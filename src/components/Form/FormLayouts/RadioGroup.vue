<template>
  <div class="my-5">
    <h2>{{question}}</h2>
    <div class="flex flex-wrap">
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
import { CalendarIcon, BriefcaseIcon, CogIcon, CursorClickIcon } from '@heroicons/vue/outline'
import RadioOption from '../FormInputs/RadioOption'

export default {
  components: {
    RadioOption
  },

  data () {
    return {
      options: {
        door: { id: 'door', label: 'By the Front Door', icon: CalendarIcon, active: true },
        wall: { id: 'wall', label: 'On an External Wall', icon: BriefcaseIcon, active: false },
        stairs: { id: 'stairs', label: 'Under the Stairs', icon: CogIcon, active: false },
        other: { id: 'other', label: 'Somewhere else', icon: CursorClickIcon, active: false }
      }
    }
  },

  props: {
    question: {
      required: true,
      type: String
    }
  },

  methods: {
    setActive (event) {
      const optionClicked = event.id
      Object.keys(this.options).forEach(option => this.options[option].active = false)
      this.options[optionClicked].active = true
    }
  }
}
</script>
