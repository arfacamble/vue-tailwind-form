<template>
  <div :class="divClass">
    <span v-if="complete">
      <CheckIcon
        class="h-8 w-8 text-white"
      />
    </span>
    <span v-if="complete === false">
      <div
        :class="[current ? 'text-purple-500' : 'text-gray-500', 'h-8 w-8 flex justify-center items-center']"
      >
        {{order}}
      </div>
    </span>
  </div>
</template>

<script>
  import { CheckIcon } from '@heroicons/vue/outline'

  export default {
    props: {
      order: {
        type: Number
      },
      complete: {
        required: true,
        type: Boolean
      },
      current: {
        required: true,
        type: Boolean
      }
    },

    components: {
      CheckIcon
    },

    computed: {
      divClass () {
        let classes = "h-10 w-10 flex justify-center items-center rounded-full"
        if (this.complete) {
          classes += " bg-purple-500"
        } else {
          classes += " border-2 border-gray-300"
        }
        if (this.current) {
          classes += " border-indigo-500"
        }
        return classes
      }
    }
  }
</script>
