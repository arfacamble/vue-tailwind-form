<template>
  <div
    class="rounded bg-gray-50 flex p-2 h-24 w-5/6 md:w-3/5 xl:w-2/5 m-2"
    :class="selected ? 'ring-1 ring-offset-2 ring-indigo-500' : ''"
    @click="toggleSelected"
  >
    <img src="../../../assets/charger_cable.png" alt="" class="m-1 h-7/8">
    <div class="flex flex-col justify-center flex-grow px-2">
      <p class="font-semibold">{{title}}</p>
      <p class="text-sm">£{{price}}</p>
    </div>
    <div
      class="h-6 w-6 cursor-pointer rounded-full bg-white my-auto mr-2 border-gray-100 border"
    >
      <div
        v-if="selected"
        class="h-full y-full rounded-full bg-indigo-500 border-2 border-white"
      >
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      title: {
        required: true,
        type: String
      },
      price: {
        required: true,
        type: String
      },
      id: {
        required: true,
        type: String
      },
      selected: {
        type: Boolean
      }
    },

    methods: {
      toggleSelected () {
        const setSelectedTo = (this.selected ? false : true)
        this.$emit('toggle-product', [this.id, setSelectedTo])
      }
    }
  }
</script>
