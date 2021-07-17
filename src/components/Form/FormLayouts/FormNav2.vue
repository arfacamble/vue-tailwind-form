<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <nav class="space-y-1" aria-label="Sidebar">
    <a
      v-for="tab in tabs"
      :key="tab.id"
      :data-id="tab.id"
      :class="[tab.current ? 'bg-gray-200 text-gray-900' : 'text-gray-600 hover:bg-gray-50 hover:text-gray-900', 'flex items-center pl-3 pr-2 py-2 text-sm font-medium rounded-md cursor-pointer']"
      :aria-current="tab.current ? 'page' : undefined"
      @click.prevent="setActiveTab"
    >
      <NavIcon
        :order="tab.order"
        :complete="tab.complete"
        :current="tab.current"
        class="mr-3"
      />
      <span class="truncate flex-grow sr-only md:not-sr-only">
        {{ tab.title }}
      </span>
    </a>
  </nav>
</template>

<script>
  import NavIcon from '../General/NavIcon'

  export default {
    components: {
      NavIcon
    },

    props: {
      tabs: {
        required: true,
        type: Object
      }
    },

    methods: {
      setActiveTab (event) {
        this.$emit('select-tab', event.currentTarget.dataset.id)
      }
    }
  }
</script>
