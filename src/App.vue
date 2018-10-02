<template>
  <div id="app">
    <product v-for="prod in list" v-bind:prod="prod"/>

  </div>
</template>

<script>
import product from './components/product.vue';
const axios = require('axios');
//
export default {
  data(){
   return {
      list:[]
    }
  },
  name: 'app',
  components: {
    product
  },
  mounted(){
    axios
      .get('./products.json')
      .then(response => {
          this.list = response.data;
          });
  }
};
</script>

<style scoped>
</style>
