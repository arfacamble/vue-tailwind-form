<!--
<template>
  <div>
    <label for="email" class="sr-only">Email</label>
    <input type="text" name="email" id="email" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="you@example.com" />
  </div>
</template>
-->

<template>
  <div class="w-full md:w-2/4 mx-auto p-4">
    <label :for="input_purpose" :class="labelClass">{{input_purpose}}</label>
    <div :class="label_display ? 'mt-1' : ''">
      <input
        type="text"
        :name="input_purpose"
        :id="input_purpose"
        class="p-2 shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md"
        :placeholder="placeholder"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    input_purpose: {
      required: true,
      type: String
    },
    id: {
      required: true,
      type: String
    },
    placeholder: {
      required: true,
      type: String
    },
    label_display: {
      required: true,
      type: Boolean
    }
    // another prop for color given focus classes?
    // or hardcoded our own color as consistent across app?
  },
  computed: {
    labelClass () {
      return (this.label_display ? "block text-sm font-medium text-gray-700" : "sr-only")
    }
  }
}
</script>
