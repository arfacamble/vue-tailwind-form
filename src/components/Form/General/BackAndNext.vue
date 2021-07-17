<template>
  <div class="flex justify-end mb-16">
    <div v-if="displayBack" class="flex items-center mx-3" data-direction="back" @click="handleClick">
      <ArrowNarrowLeftIcon
        :class="iconClass"
      />
      <span class="text-sm text-indigo-500">Back</span>
    </div>
    <div v-if="displayNext" class="flex items-center mx-3" data-direction="next" @click="handleClick">
      <span class="text-sm text-indigo-500">Next</span>
      <ArrowNarrowRightIcon
        :class="iconClass"
      />
    </div>
  </div>
</template>

<script>
  import { ArrowNarrowRightIcon, ArrowNarrowLeftIcon } from '@heroicons/vue/outline'

  export default {
    props: {
      displayBack: { type: Boolean },
      displayNext: { type: Boolean },
      disableNext: { type: Boolean },
    },

    components: {
      ArrowNarrowRightIcon,
      ArrowNarrowLeftIcon
    },

    computed: {
      iconClass () {
        return "h-5 w-5 border border-gray-500 rounded-full mx-3 text-indigo-500"
      }
    },

    methods: {
      handleClick (event) {
        this.$emit('navigate', event.currentTarget.dataset.direction)
      }
    }
  }
</script>
