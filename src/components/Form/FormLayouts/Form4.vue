<template>
  <div class="container mx-auto pt-3 flex flex-wrap justify-evenly">
    <ChargerCard
      v-for="charger in chargers"
      :key="charger.id"
      :colour="charger.colour"
      :id="charger.id"
      :price="charger.price"
    />
  </div>
</template>

<script>
  import ChargerCard from '../FormInputs/ChargerCard'

  export default {
    components: {
      ChargerCard
    },

    data () {
      return {
        chargers: [
          { id: 'blue', colour: 'Blue', price: '799'},
          { id: 'red', colour: 'Red', price: '799'},
          { id: 'yellow', colour: 'Yellow', price: '799'},
          { id: 'black', colour: 'Black', price: '799'},
          { id: 'white', colour: 'White', price: '799'},
          { id: 'green', colour: 'Green', price: '799'}
        ]
      }
    }
  }
</script>
