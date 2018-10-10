<template>
	<div id="test">
		<b-button variant="primary" @click="test1">PUSH</b-button>
		<b-button class="ml-2" variant="primary" @click="test2">START</b-button>
		<h1>msg: {{addStart}} + {{start}}</h1>
	</div>
</template>
<script>
	export default {
		name:'test',
  		data(){
   			return {
   				msg:0,
   				count:0,
   				start:0,
   				onPage:0
    		}
  		},
  		computed:{
  			addStart(){
  				this.msg = this.onPage;
  				return this.msg;
  			}
  		},
  		methods:{
  			test1(){
  				this.onPage++;
  			},
  			test2(){
  				let qwerty = this.onPage;
  				this.start = this.start + this.onPage;
  			}
  		}
   	};
</script>
<style>
	
</style>