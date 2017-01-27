<template>
  <div id="app">
    <h1>Score 1: <span class="counter">{{ displayedValue }}</span></h1>
    <button v-on:click="up">Up</button>
    <button v-on:click="down">Down</button>
    <button v-on:click="get">Get</button>
    <input type="number" v-model="inputField">
    <button v-on:click="set">Set</button>
    <button v-on:click="reset">Reset</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      counters: [{
        value: 0,
        format: 4,
        inputField: ''
      }]
    }
  },

  computed: {
    displayedValue() {
      return new Array(this.format-(this.value+"").length+1).join(0) + this.value;
    }
  },

  methods: {
    up(e) {
      e.preventDefault();
      if (this.value < (Math.pow(10, this.format)-1)) {
        this.value++;
      }
    },
    down(e) {
      e.preventDefault();
      if (this.value > 0) {
        this.value--;
      }
    },

    get(e) {
      e.preventDefault();
      alert(this.value);
    },

    set(e) {
      e.preventDefault();
      if(this.inputField > (Math.pow(10, this.format) -1)) {
        this.value = this.value;
      } else {
        this.value = Math.trunc(this.inputField);
      }
    },

    reset(e) {
      e.preventDefault();
      this.value = 0;
    }
  }
}
</script>
