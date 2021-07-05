<template>
  <div>
    <label :for="input_purpose" class="block text-sm font-medium text-gray-700">{{input_purpose}}</label>
    <select
      :id="input_purpose"
      :name="input_purpose"
      class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md"
      @change="changeSelected($event)"
    >
      <option
        v-for="option in options"
        :key="option"
        :value="option"
        :selected="isOptionSelected(option)"
      >
        {{option}}
      </option>
      <option>USA</option>
      <option selected="">Canada</option>
      <option>EU</option>
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
  data: {
    selected_option: null
  },
  methods: {
    changeSelected (event) {
      this.selected_option = event.target.value
    }
  },
  computed: {
    // does this function run at the point at which the option element is created/mounted?
    // or once for the SelectDropdown component?
    isOptionSelected (option) {
      option === this.selected_option
    }
  }
}
</script>
