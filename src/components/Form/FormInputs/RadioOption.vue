<template>
  <div
    class="w-2/5 lg:w-1/5 m-4 flex flex-col items-center p-2 rounded-md"
    @click="setActive"
    :class="[active ? 'ring-1 ring-offset-2 ring-indigo-500' : '', 'relative block rounded-lg border border-gray-300 bg-white shadow-sm px-6 py-4 cursor-pointer hover:border-gray-400 sm:flex sm:justify-between focus:outline-none']"
  >
    <component
      v-if="icon"
      :is="icon"
      class="text-gray-400 w-2/5"
    >
    </component>
    <p class="text-gray-400 text-center">{{label}}</p>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String
    },
    label: {
      type: String
    },
    icon: {
      type: undefined
    },
    active: {
      type: Boolean
    }
  },

  methods: {
    setActive () {
      this.$emit('set-active', this.id)
    }
  }
}
</script>
