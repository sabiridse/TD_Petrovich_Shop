<template>
  <div id="app">
    <navbar/>
    <h1>start: {{compStart}} end: {{compEnd}}</h1>
    <product v-for="prod in addListLimit" v-bind:prod="prod"/>
  </div>
</template>

<script>
import product from './components/product.vue';
import navbar from './components/navbar.vue';
import test from './components/test.vue';
const axios = require('axios');
const async = require('async');
import eventbus from './plugins/eventbus.js';
//
export default {
  data(){
   return {
      listAll:[],
      listLimit:[],
      onPageCount:10,
      searchData:'',
      start:0,
      end:10,
      prev:1,
      next:0
    }
  },
  name: 'app',
  components: {
    product,
    navbar,
    test
  },
  async  mounted(){
    await axios
      .get('./products.json')
      .then(response => {
          this.listAll = response.data;
          });
  },
  created(){
    eventbus.$on('switchPage',this.switchPage);
    eventbus.$on('onPage',this.onPage);
    eventbus.$on('search',this.search);
  },
  computed:{
    addListLimit(){
      this.listLimit = this.listAll
                            .filter(prod => prod.title.toLowerCase().indexOf(this.searchData
                            .toLowerCase()) !=-1)
                            .slice(this.compStart,this.compEnd);
      return this.listLimit;
    },
    compStart(){
        return this.start = this.start < 0 ? 0 : this.start;
      },
    compEnd(){
        // return this.end = this.end >= this.listAll.length ? this.listAll.length : this.start + this.onPageCount;
        return this.end = this.start + this.onPageCount;
    },
    prevDisable(){    
      return this.prev = this.start <= 0 ? 1 : 0;
    },
    nextDisable(){
      return this.next = this.compEnd >= this.listAll.length ? 1 : 0;
    }
  },
  methods:{
    switchPage(value){
      this.pageNumber = value; 
      this.start = this.start + value*this.onPageCount;
      eventbus.$emit('disabling',{prev:this.prevDisable,
                                  next:this.nextDisable});
    },
    onPage(value){
      this.onPageCount = value;
      eventbus.$emit('disabling',{prev:this.prevDisable,
                                  next:this.nextDisable});
    },
    search(value){
      this.searchData = value;
      this.pageNumber = 0;
    }
  }
};
</script>

<style scoped>
</style>
