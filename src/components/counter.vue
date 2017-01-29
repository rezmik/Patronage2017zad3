<template>
   <div id="app">
     <!--<h1> Value: {{ currentValue }}, Format: {{ currentFormat }}</h1>-->
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
       currentValue: this.value,
       currentFormat: this.format
        //inputField: ''
     }
   },

   props: ["value", "format"],

   computed: {
     displayedValue() {
       return new Array(this.currentFormat-(this.currentValue+"").length+1).join(0) + this.currentValue;
     }
   },

   methods: {
     up(e) {
       e.preventDefault();
       if (this.currentValue < (Math.pow(10, this.currentFormat)-1)) {
         this.currentValue++;
       }
     },
     
     down(e) {
       e.preventDefault();
       if (this.currentValue > 0) {
         this.currentValue--;
       }
     },

     get(e) {
       e.preventDefault();
       alert(this.currentValue);
     },

     set(e) {
       e.preventDefault();
       if(this.inputField > (Math.pow(10, this.currentFormat) -1)) {
         this.currentValue = this.currentValue;
       } else {
         this.currentValue = Math.trunc(this.inputField);
       }
     },

     reset(e) {
       e.preventDefault();
       this.currentValue = 0;
     }
   }
 }
 </script>
