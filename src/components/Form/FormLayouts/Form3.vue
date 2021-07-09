<template>
  <div class="container mx-auto pt-3">
    <Button
      v-for="button in buttons"
      :key="button.text"
      :text="button.text"
      :larger="button.larger"
      :icon="button.icon"
    />
  </div>
</template>

<script>
  import { MailIcon } from '@heroicons/vue/solid'
  import Button from '../General/Button'

  export default {
    components: {
      Button
    },

    data () {
      return {
        buttons: [
          { text: 'Submit' },
          { text: 'Banana', larger: true},
          { text: 'Yes', icon: MailIcon},
          { text: 'NO', larger: true, icon: MailIcon}
        ]
      }
    }
  }
</script>
