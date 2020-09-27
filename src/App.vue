<template>
  <div id="app">
    <h1>時間をきれいに表示するよ！</h1>
    <div class="jumbotron">
      <div class="row">
        <h1 class="display-4">World Clock by Vue.js</h1>
        <CitySelector v-on:addcity="addcity"/>
      </div>
    </div>

    <div class="container">
      <div class="card-deck">
        <div class="card shadow" v-for="city in cities" :key="city" style="min-width:18rem; max-width18rem;">
          <Clock :city="city" v-on:delcity="delcity"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Clock from './components/Clock.vue';
import CitySelector from './components/CitySelector.vue';

export default {
  name: 'App',
  components:{
    Clock,
    CitySelector
  },
  data(){
    return{
      cities:["Asia/Tokyo","America/New_York","Europe/london"]
    }
  },
  methods:{
    addcity(city){
      if(city){
      this.cities.push(city);
      }
    },
    delcity(city){
      let i = this.cities.indexOf(city)
      if(i >= 0){
        this.cities.splice(i, 1)
      }
    }
  }
}
</script>

<style scoped>
h1{color:limegreen;}
h2{color:mediumaquamarine}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
