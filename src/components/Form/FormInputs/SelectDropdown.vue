<template>
  <div class="w-full mx-auto p-4 md:w-2/4">
    <label :for="input_purpose" class="block text-sm font-medium text-gray-700">{{input_purpose}}</label>
    <select
      :id="input_purpose"
      :name="input_purpose"
      class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md shadow-sm"
    >
      <option disabled selected hidden>Select Material...</option>
      <option
        v-for="option in options"
        :key="option"
        :value="option"
      >
        {{option}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    input_purpose: {
      required: true,
      type: String
    },
    options: {
      required: true,
      type: Array
    }
  },
  data () {
    return {
      selected_option: null
    }
  }
}
</script>
