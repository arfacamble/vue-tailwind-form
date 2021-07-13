<template>
  <div class="card-container relative w-2/5 md:w-1/4 lg:w-1/5 h-48 flex flex-col justify-end m-3">
    <img src="../../../assets/charger.png" alt="" class="absolute mx-auto h-3/5 inset-0">
    <div class="bg-gray-50 w-full h-3/4 flex flex-col justify-end items-center rounded p-2">
      <p class="mb-1">{{colour}}</p>
      <p class="text-sm">£{{price}}</p>
      <a href="#" class="text-blue-500 text-sm">More Info</a>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      colour: {
        required: true,
        type: String
      },
      price: {
        required: true,
        type: String
      }
    }
  }
</script>
