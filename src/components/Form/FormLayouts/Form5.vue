<template>
  <div class="container mx-auto">
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :id="product.id"
      :price="product.price"
      :title="product.title"
      :selected="product.selected"
      @toggle-product="toggleProduct"
    />
  </div>
</template>

<script>
  import ProductCard from '../FormInputs/ProductCard'

  export default {
    components: {
      ProductCard
    },

    data () {
      return {
        products: {
          chargerCable: { id: 'chargerCable', title: "Charger Cable", price: "149", selected: false },
          charger: { id: 'charger', title: "Charger Cable XL", price: "179", selected: false }
        },
        selected: []
      }
    },

    methods: {
      toggleProduct (payload) {
        const id = payload[0]
        const setSelectedTo = payload[1]
        this.products[id].selected = setSelectedTo
      }
    }
  }
</script>
