<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <nav class="space-y-1" aria-label="Sidebar">
    <a
      v-for="tab in tabs"
      :key="tab.id"
      href=""
      :data-id="tab.id"
      :class="[tab.current ? 'bg-gray-200 text-gray-900' : 'text-gray-600 hover:bg-gray-50 hover:text-gray-900', 'flex items-center px-3 py-2 text-sm font-medium rounded-md']"
      :aria-current="tab.current ? 'page' : undefined"
      @click.prevent="setActiveTab"
    >
      <component
        :is="tab.icon"
        :class="[tab.current ? 'text-gray-500' : 'text-gray-400', 'flex-shrink-0 -ml-1 mr-3 h-6 w-6']"
        aria-hidden="true"
      />
      <span class="truncate flex-grow">
        {{ tab.name }}
      </span>
      <span
        v-if="tab.complete"
        :class="[tab.current ? 'text-gray-500' : 'text-gray-400', 'flex-shrink-0 -mr-1 ml-3 h-6 w-6']"
      >
        <CheckIcon />
      </span>
    </a>
  </nav>
</template>

<script>
  import { CalendarIcon, ChartBarIcon, FolderIcon, HomeIcon, InboxIcon, UsersIcon, CheckIcon } from '@heroicons/vue/outline'

  export default {
    components: {
      CheckIcon
    },

    data () {
      return {
        tabs: [
          { id: 'installationDetails', name: 'Installation Details', href: '#', icon: HomeIcon, current: false, complete: true },
          { id: 'grantInformation', name: 'Grant Information', href: '#', icon: UsersIcon, current: false, complete: true },
          { id: 'projects', name: 'Projects', href: '#', icon: FolderIcon, current: true, complete: false },
          { id: 'calendar', name: 'Calendar', href: '#', icon: CalendarIcon, current: false, complete: false },
          { id: 'documents', name: 'Documents', href: '#', icon: InboxIcon, current: false, complete: false },
          { id: 'reports', name: 'Reports', href: '#', icon: ChartBarIcon, current: false, complete: false },
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
