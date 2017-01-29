<template>
  <div class="container" id="app">
    <div class="panel panel-default">
      <div class="panel-body">
        <div class="col-sm-1">Value:</div>
        <div class="col-sm-4">
          <input class="form-control" type="number" v-model="value">
        </div>
        <div class="col-sm-1">Format:</div>
        <div class="col-sm-4">
          <input class="form-control" type="number" v-model="format">
        </div>
        <div class="col-sm-2">
          <button class="btn btn-success" v-on:click="addCounter">Add</button>
        </div>
      </div>
    </div>
   <counter v-for="counter in counters" :value="counter.value" :format="counter.format"
      v-on:remove="removeCounter(counter)"
      :key="counter.id"></counter>
 </div>
</template>

<script>
 import Counter from './components/Counter.vue'

 export default {
   name: 'app',
   data () {
     return {
       value: '',
       format: '',
       counters: [
         {
           value: 100,
           format: 4,
           id: Math.random()
         },
         {
           value: 10,
           format: 3,
           id: Math.random()
         }
       ]
     }
   },

   components: {
     'counter': Counter
   },

   methods: {
     addCounter(e) {
       let Counter = {
         value: this.value,
         format: this.format,
         id: Math.random()
       }
       this.counters.push(Counter)
     },

     removeCounter(counter, id) {
       this.counters.splice(id,1)
     }
   }
 }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
