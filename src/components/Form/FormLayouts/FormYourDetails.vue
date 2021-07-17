<template>
  <div class="h-full w-full px-12 pt-8 flex flex-col">
    <h1 class="text-3xl">Your Details</h1>
    <div class="border flex-1 p-8">
      <!-- <FormYourDetails1 @update-form-data="updateResults" /> -->
      <QuestionsRender v-if="currentStep === 1" :formId="'yd1'" :questions="formData.yd1" @update-form-data="updateFormData"/>
      <QuestionsRender v-if="currentStep === 2" :formId="'yd2'" :questions="formData.yd2" @update-radio-active="updateRadioActive"/>
    </div>
    <ProgressBar :steps="steps" />
    <BackAndNext :displayNext="true" :displayBack="true" @navigate="changeStep"/>
  </div>
</template>

<script>
  import ProgressBar from '../General/ProgressBar'
  import BackAndNext from '../General/BackAndNext'
  import QuestionsRender from './QuestionsRender'
  import { CalendarIcon, BriefcaseIcon, CogIcon, CursorClickIcon } from '@heroicons/vue/outline'

  export default {
    components: {
      ProgressBar,
      BackAndNext,
      QuestionsRender
    },

    data () {
      return {
        currentStep: 1,
        steps: {
          1: { id: 1, status: 'current' },
          2: { id: 2, status: 'pending' },
          3: { id: 3, status: 'pending' },
          4: { id: 4, status: 'pending' },
          5: { id: 5, status: 'pending' }
        },
        formData: {
          yd1: {
            firstName: { component: 'textInput', id: 'firstName', value: '', input_purpose: 'First Name', placeholder: 'First Name', label_display: false, half_width: true },
            lastName: { component: 'textInput', id: 'lastName', value: '', input_purpose: 'Last Name', placeholder: 'Last Name', label_display: false, half_width: true },
            email: { component: 'textInput', id: 'email', value: '', input_purpose: 'Email', placeholder: 'Email', label_display: false, half_width: true },
            contactNumber: { component: 'textInput', id: 'contactNumber', value: '', input_purpose: 'Contact Number', placeholder: 'Contact Number', label_display: false, half_width: true },
            houseNumber: { component: 'textInput', id: 'houseNumber', value: '', input_purpose: 'House Number', placeholder: 'House Number', label_display: false, half_width: true },
            postcode: { component: 'textInput', id: 'postcode', value: '', input_purpose: 'Postcode', placeholder: 'Postcode', label_display: false, half_width: true },
            address: { component: 'textInput', id: 'address', value: '', input_purpose: 'Address', placeholder: 'Address', label_display: false }
          },
          yd2: {
            fuseBoardLocation: {
              component: 'radioGroup', id: 'fuseBoardLocation', value: '', question: "Where is your fuse board located?",
              options: {
                door: { id: 'door', label: 'By the Front Door', icon: CalendarIcon, active: false },
                wall: { id: 'wall', label: 'On an External Wall', icon: BriefcaseIcon, active: false },
                stairs: { id: 'stairs', label: 'Under the Stairs', icon: CogIcon, active: false },
                other: { id: 'other', label: 'Somewhere else', icon: CursorClickIcon, active: false }
              }
            }
          }
        }
      }
    },

    methods: {
      changeStep (direction) {
        if (direction === 'next' && this.currentStep < Object.keys(this.steps).length) {
          this.steps[this.currentStep].status = 'complete'
          const nextStep = this.currentStep + 1
          this.steps[nextStep].status = 'current'
          this.currentStep = nextStep
        }
      },
      updateFormData (payload) {
        this.formData[payload.formId][payload.inputId].value = payload.value
        this.sendResults()
      },
      updateRadioActive (payload) {
        const formId = payload.formId
        const inputId = payload.inputId
        Object.keys(this.formData[formId][inputId].options).forEach((key) => {
          this.formData[formId][inputId].options[key].active = false
        })
        this.formData[formId][inputId].options[payload.setActive].active = true
      },
      sendResults () {
        const results = {}
        Object.keys(this.formData.yd1).forEach((key) => {
          results[key] = this.formData.yd1[key].value
        })
        console.log(results)
      }
      // updateResults (payload) {
      //   const formKey = payload[0]
      //   const formData = payload[1]
      //   this.results[formKey] = formData
      //   // console.log(this.results)
      // }
    }
  }
</script>
