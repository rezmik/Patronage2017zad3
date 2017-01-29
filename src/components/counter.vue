<template>
  <div class="panel panel-default panelMargin">
       <h1>
         Score:
         <span class="counter">{{ displayedValue }}</span>
         <button class="btn btn-danger pull-right">Delete</button>

       </h1>
       <div class="panel-body">
         <div class="col-sm-offset-1 col-sm-3">
           <button class="btn btn-primary" v-on:click="up">Up</button>
           <button class="btn btn-primary"v-on:click="down">Down</button>
           <button class="btn btn-primary"v-on:click="get">Get</button>
         </div>
         <div class="col-sm-4">
           <input class="form-control" type="number" v-model="inputField">
         </div>
         <div class="col-sm-2">
           <button class="btn btn-primary"v-on:click="set">Set</button>
           <button class="btn btn-primary"v-on:click="reset">Reset</button>
         </div>
         <div class="col-sm-2"></div>
       </div>
   </div>
</template>

<script>
 export default {
   name: 'app',
   data () {
     return {
       currentValue: this.value,
       currentFormat: this.format,
       inputField: ''
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

 <style>
   .panelMargin {
     padding-right: 15px;
   }
 </style>
