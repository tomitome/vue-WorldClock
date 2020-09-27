<template>
	<div>
		<div class="card-header text-white bg-primary text-center h2">
		{{ shortName }}
		<button class="btn text-white" @click="delcity">
			<i class="fas fa-trash-alt"></i>
		</button>
		</div>
		<div class="card-body h1">{{time}}</div>
	</div>
</template>

<script>
export default {
	props:['city'],
	data(){
		return{
			time :new Date().toLocaleTimeString(),
		}
	},
	mounted(){
		setInterval(() =>{
			this.time = new Date().toLocaleTimeString('ja',{timeZone:this.city})
		},1000)
	},
	computed:{
		shortName(){
			var p =this.city.indexOf("/")+1
			return this.city.substring(p).replace("_"," ")
		}
	},
	methods: {
		delcity(){
			this.$emit("delcity", this.city);
		}
	}
}
</script>

<style scoped>
h1{
	margin: 40px 0 0;
	color: blue;
}
</style>