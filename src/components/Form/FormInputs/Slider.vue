<template>
  <div class="w-7/8 lg:w-3/5 xl:w-2/5">
    <label v-if="question" :for="question" class="block text-sm font-medium text-gray-700">
      {{question}}
    </label>
    <div class="flex my-3">
      <span class="mr-3 text-gray-500">{{min}}</span>
      <input
        ref="input"
        v-model="currentValue"
        type="range"
        :min="min"
        :max="max"
        class="slider flex-grow"
        @input="emitValue"
      >
      <span class="ml-3 text-gray-500">{{max}}</span>
    </div>
    <p class="w-full text-center text-sm font-medium text-gray-700">{{currentValue}} metres</p>
  </div>
</template>

<script>
  export default {
    props: {
      id: {
        required: true,
        type: String
      },
      min: {
        required: true,
        type: Number
      },
      max: {
        required: true,
        type: Number
      },
      value: {
        required: true,
        type: Number
      },
      question: {
        type: String
      }
    },

    data () {
      return {
        currentValue: this.value
      }
    },

    methods: {
      emitValue () {
        this.$emit('update-value', [this.id, parseInt(this.currentValue)])
      }
    }
  }
</script>

<style scoped>
  /* remove all default styles */
  input[type=range] {
    -webkit-appearance: none; /* Hides the slider so that custom slider can be made */
    width: 100%; /* Specific width is required for Firefox. */
    background: transparent; /* Otherwise white in Chrome */
  }

  input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
  }

  input[type=range]:focus {
    outline: none; /* Removes the blue border. You should probably do some kind of focus styling for accessibility reasons though. */
  }

  input[type=range]::-ms-track {
    width: 100%;
    cursor: pointer;

    /* Hides the slider so custom styles can be added */
    background: transparent;
    border-color: transparent;
    color: transparent;
  }

  /* style the thumb/circle for each browser */
  input[type=range]::-webkit-slider-thumb {
    border: 2px solid blue;
    height: 24px;
    width: 24px;
    border-radius: 50%;
    background: #ffffff;
    cursor: pointer;
    margin-top: -7px; /* You need to specify a margin in Chrome, but in Firefox and IE it is automatic */
  }

  input[type=range]::-moz-range-thumb {
    border: 2px solid blue;
    height: 24px;
    width: 24px;
    border-radius: 50%;
    background: #ffffff;
    cursor: pointer;
  }

  /* might need further styles for internet explorer,
  working for me in edge */
  /* input[type=range]::-ms-thumb {
    border: 2px solid blue;
    height: 24px;
    width: 24px;
    border-radius: 50%;
    background: #ffffff;
    cursor: pointer;
  } */

  /* style the runner/track */
  input[type=range]::-webkit-slider-runnable-track {
    width: 100%;
    height: 8.4px;
    cursor: pointer;
    background: lightgray;
  }

  input[type=range]::-moz-range-track {
    width: 100%;
    height: 8.4px;
    cursor: pointer;
    background: lightgray;
  }

  /* if track needs styling in IE, it's super gross
  below is a copy paste of example styles,
  I can update for our styles if need be*/

  /* input[type=range]::-ms-track {
    width: 100%;
    height: 8.4px;
    cursor: pointer;
    background: transparent;
    border-color: transparent;
    border-width: 16px 0;
    color: transparent;
  }
  input[type=range]::-ms-fill-lower {
    background: #2a6495;
    border: 0.2px solid #010101;
    border-radius: 2.6px;
    box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  }
  input[type=range]:focus::-ms-fill-lower {
    background: #3071a9;
  }
  input[type=range]::-ms-fill-upper {
    background: #3071a9;
    border: 0.2px solid #010101;
    border-radius: 2.6px;
    box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  }
  input[type=range]:focus::-ms-fill-upper {
    background: #367ebd;
  } */

</style>
