<template>
  <div id="app">
    <navbar/>
    <product v-for="prod in listLimit" v-bind:prod="prod"/>
  </div>
</template>

<script>
import product from './components/product.vue';
import navbar from './components/navbar.vue';
const axios = require('axios');
const async = require('async');
//
export default {
  data(){
   return {
      listAll:[],
      listLimit:[]
    }
  },
  name: 'app',
  components: {
    product,
    navbar
  },
  async  mounted(){
    await axios
      .get('./products.json')
      .then(response => {
          this.listAll = response.data;
          });
      for (let i=0; i < 20; i++){
        this.listLimit.push(this.listAll[i]);
      };
  }
};
</script>

<style scoped>
</style>
