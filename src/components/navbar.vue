<template>
<b-navbar toggleable="md" type="dark" variant="info" sticky="true">
  <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
  <b-collapse is-nav id="nav_collapse">
    <b-navbar-nav>
      <b-nav-item :disabled="prevDisable == 1" @click="switchPage(-1)">НАЗАД</b-nav-item>
      <b-nav-item :disabled="nextDisable == 1" @click="switchPage(1)">ВПЕРЁД</b-nav-item>
      <b-nav-item-dropdown text="Показать" right>
        <b-dropdown-item @click="onPage(10)">10 на странице</b-dropdown-item>
        <b-dropdown-item @click="onPage(20)">20 на странице</b-dropdown-item>
        <b-dropdown-item @click="onPage(50)">50 на странице</b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>
    <b-navbar-nav class="ml-auto">
        <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Поиск" v-model="key" @input="search(key)"/>      
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
</template>
<script>
import eventbus from '../plugins/eventbus.js';
	export default {
    data(){
      return {
        key:'',
        prevDisable:1,
        nextDisable:0

      }
    },
    created(){
    eventbus.$on('disabling',this.disabling);
  },
    methods:{
      switchPage(param){
        eventbus.$emit('switchPage',param);
      },
      onPage(param){
        eventbus.$emit('onPage',param);
      },
      search(param){
        eventbus.$emit('search',param);
      },
      disabling(param){
        this.prevDisable = param.prev;
        this.nextDisable = param.next;
      }
    }
  };
</script>
<style scoped>

</style>