<template>
   <counter v-for="counter in counters" :value="counter.value" :format="counter.format"></counter>
</template>

<script>
 import Counter from './components/Counter.vue'

 export default {
   name: 'app',
   data () {
     return {
       counters: [
         {
           value: 100,
           format: 4
         },
         {
           value: 10,
           format: 3
         }
       ]
     }
   },

   components: {
     'counter': Counter
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
