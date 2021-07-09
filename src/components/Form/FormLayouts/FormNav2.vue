<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <nav class="space-y-1" aria-label="Sidebar">
    <a
      v-for="tab in tabs"
      :key="tab.id"
      href=""
      :data-id="tab.id"
      :class="[tab.current ? 'bg-gray-200 text-gray-900' : 'text-gray-600 hover:bg-gray-50 hover:text-gray-900', 'flex items-center pl-3 pr-2 py-2 text-sm font-medium rounded-md']"
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
        {{ tab.name }}
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

    data () {
      return {
        tabs: [
          { order: 1, id: 'installationDetails', name: 'Installation Details', href: '#', current: false, complete: true },
          { order: 2, id: 'grantInformation', name: 'Grant Information', href: '#', current: false, complete: true },
          { order: 3, id: 'projects', name: 'Projects', href: '#', current: true, complete: false },
          { order: 4, id: 'calendar', name: 'Calendar', href: '#', current: false, complete: false },
          { order: 5, id: 'documents', name: 'Documents', href: '#', current: false, complete: false },
          { order: 6, id: 'reports', name: 'Reports', href: '#', current: false, complete: false },
        ]
      }
    },

    methods: {
      setActiveTab (event) {
        this.tabs.forEach(tab => tab.current = false)
        const tabSelected = this.tabs.find(tab => tab.id === event.currentTarget.dataset.id)
        const tabIndex = this.tabs.findIndex(tab => tab === tabSelected)
        tabSelected.current = true
        this.tabs.tabIndex = tabSelected
        this.$emit('select-tab', tabSelected)
      }
    }
  }
</script>
