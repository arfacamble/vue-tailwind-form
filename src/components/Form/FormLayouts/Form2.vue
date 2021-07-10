<template>
  <div class="container mx-auto">
    <RadioGroup
      :question="firstQuestion"
      :options="optionsWithIcons"
      @set-active="setActive"
    />
    <TextInput
      v-if="optionsWithIcons.other.active"
      :input_purpose="moreInfoIfOther.input_purpose"
      :id="moreInfoIfOther.id"
      :placeholder="moreInfoIfOther.placeholder"
      :full_width="moreInfoIfOther.full_width"
    />
    <DragAndDrop
      :hint="'Show us PLEASE'"
    />
    <div class="flex flex-col items-center py-8">
      <Slider
        :min="0"
        :max="10"
        :value="5"
        :id="'sliderNumber'"
        :question="'How large is the number you want to tell us about?'"
        @update-value="updateFormData"
      />
      <br>
      <Slider
        :min="0"
        :max="100"
        :value="50"
        :id="'slider2'"
        @update-value="updateFormData"
      />
    </div>
    <RadioGroup
      :question="secondQuestion"
      :options="optionsNoIcons"
      @set-active="setActive"
    />
  </div>
</template>

<script>
import RadioGroup from './RadioGroup'
import TextInput from '../FormInputs/TextInput'
import DragAndDrop from '../FormInputs/DragAndDrop'
import Slider from '../FormInputs/Slider'
import { CalendarIcon, BriefcaseIcon, CogIcon, CursorClickIcon } from '@heroicons/vue/outline'

export default {
  components: {
    RadioGroup,
    TextInput,
    DragAndDrop,
    Slider
  },

  data () {
    return {
      firstQuestion: 'What\'s the floor like?',
      optionsWithIcons: {
        door: { id: 'door', label: 'By the Front Door', icon: CalendarIcon, active: false },
        wall: { id: 'wall', label: 'On an External Wall', icon: BriefcaseIcon, active: false },
        stairs: { id: 'stairs', label: 'Under the Stairs', icon: CogIcon, active: false },
        other: { id: 'other', label: 'Somewhere else', icon: CursorClickIcon, active: false }
      },
      moreInfoIfOther: {
        input_purpose: 'Tell us where you want the damn thing then',
        id: 'moreInfo',
        placeholder: 'Tell us more...',
        full_width: true,
        value: ''
      },
      secondQuestion: 'Will we find bodies when installing your device?',
      optionsNoIcons: {
        yes: { id: 'yes', label: 'Yes', active: false },
        no: { id: 'no', label: 'No', active: false },
        loads: { id: 'loads', label: 'Loads!!', active: false },
        onlyAnimals: { id: 'onlyAnimals', label: 'Only Animals', active: false }
      }
    }
  },

  methods: {
    setActive (event) {
      const optionClicked = event.id
      const dataPossibilities = Object.keys(this.$data)
      const dataKey = dataPossibilities.find(key => Object.prototype.hasOwnProperty.call(this[key], optionClicked))
      Object.keys(this[dataKey]).forEach(option => this[dataKey][option].active = false)
      this[dataKey][optionClicked].active = true
    },
    updateFormData (payload) {
      const id = payload[0]
      const value = payload[1]
      console.log(`id: ${id}, value: ${value}`)
    }
  }
}
</script>
