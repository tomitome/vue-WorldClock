<template>
  <div class="col-4 font-row align-items-center">
    <div class="col-auto my-1">
      <select class="custum-select mr-sm-2" v-model="selected">
        <option v-for="city in cities" :key="city">{{city}}</option>
      </select>
    </div>
    <div class="col-auto my-1">
      <button class="btn btn-primary" v-on:click="select">追加</button>
    </div>
  </div>
</template>

<script>
let cities = [
  "Europe/Madrid","Europe/Zurich","Europe/London",
];

export default {
  data(){
    return{
      cities: cities,
      selected: '',
    }
  },
  methods: {
    select(){
      this.$emit('addcity',this.selected)
    }
  }
};
</script>