<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <nav class="flex items-center justify-center my-2" aria-label="Progress">
    <p class="text-sm font-medium">Step {{ currentStep }} of {{ stepCount }}</p>
    <ol class="ml-8 flex items-center space-x-5">
      <li v-for="step in steps" :key="step.id">
        <a v-if="step.status === 'complete'" class="block w-2.5 h-2.5 bg-indigo-600 rounded-full hover:bg-indigo-900">
          <span class="sr-only">{{ step.name }}</span>
        </a>
        <a v-else-if="step.status === 'current'" class="relative flex items-center justify-center" aria-current="step">
          <span class="absolute w-5 h-5 p-px flex" aria-hidden="true">
            <span class="w-full h-full rounded-full bg-indigo-200" />
          </span>
          <span class="relative block w-2.5 h-2.5 bg-indigo-600 rounded-full" aria-hidden="true" />
          <span class="sr-only">{{ step.name }}</span>
        </a>
        <a v-else class="block w-2.5 h-2.5 bg-gray-200 rounded-full hover:bg-gray-400">
          <span class="sr-only">{{ step.name }}</span>
        </a>
      </li>
    </ol>
  </nav>
</template>

<script>
export default {
  props: {
    steps: { required: true, type: Object },
  },

  computed: {
    stepCount () {
      return Object.keys(this.steps).length
    },

    currentStep () {
      const steps = Object.keys(this.steps)
      return steps.find(step => this.steps[step].status === 'current')
    }
  }
}
</script>
