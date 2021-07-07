<template>
  <div class="h-screen w-full">
    <div class="container mx-auto flex-flex-wrap pt-3">
      <RadioGroup
        :question="'What\'s the floor like?'"
      />
    </div>
  </div>
</template>

<script>
import RadioGroup from './RadioGroup'

export default {
  components: {
    RadioGroup,
  }
}
</script>
