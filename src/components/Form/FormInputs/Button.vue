<template>
<div>
  <button
    type="button"
    :class="buttonClass"
  >
  <component
    v-if="icon"
    :is="icon"
    class="-ml-1 mr-3 h-5 w-5"
    aria-hidden="true"
  />
  {{ text }}
  </button>
</div>
</template>

<script>
  import { MailIcon } from '@heroicons/vue/solid'

  export default {
    props: {
      text: {
        required: true,
        type: String
      },
      icon: {
        type: undefined
      },
      larger: {
        default: false,
        type: Boolean
      }
    },
    components: {
      MailIcon
    },

    computed: {
      buttonClass () {
        return [this.larger ? 'text-base' : 'text-sm', 'm-2 inline-flex items-center px-4 py-2 border border-transparent shadow-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500']
      }
    }
  }
</script>
