<template>
  <div id="app">
<div class="column is-half is-offset-one-quarter">
    <img src="./assets/logo.png">
<hr>
  <h4 class="is-size-4">
Pokedex
</h4>
<div v-for="(poke, index) in pokemons" :key="index">

<pokemon :name="poke.name" :url="poke.url" :num="index+1"/>
</div>

  </div>
  </div>

</template>

<script>
import axios from 'axios';
import pokemon from './components/Pokemon'

export default {
  name: 'App',
  data(){
return{
  pokemons:[]
}
  },
  created:function(){
axios.get("https://pokeapi.co/api/v2/pokemon?limit=152&offset=0").then(res=>{
this.pokemons = res.data.results;

})
  },
  components: {
    pokemon
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
