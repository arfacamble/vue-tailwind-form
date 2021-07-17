<template>
  <div class>
    <div class="bg-grey-light h-1"></div>
    <div class="flex">
      <div class="flex-1" v-for="step in steps" :key="step">
        <div
          v-if="currentStep >= step"
          class="bg-blue -mt-1 h-1"
          :class="{ 'w-1/2': currentStep === step, 'w-full': currentStep < step }"
        >
        </div>
        <div
          class="-mt-3 mx-auto rounded-full h-5 w-5"
          :class="{ 'bg-blue': step <= currentStep, 'bg-grey-light': currentStep != step }"
        >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      stepCount: {
        required: true,
        type: Number
      },
      currentStep: {
        required: true,
        type: Number
      }
    },

    computed: {
      steps () {
        return [...Array(this.stepCount).keys()]
      }
    }
  }
</script>
