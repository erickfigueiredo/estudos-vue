<template>

  <div id="app">
    <div class="column is-half is-offset-one-quarter">
    <img src="./assets/erickdev.png" alt="">
    <hr>
    <h1 class="is-size-3 mb-4">PokéDex</h1>
      <div v-for="(pokemon, index) in pokemons" :key="index">
        <Pokemon :name="pokemon.name" :url="pokemon.url" :num="index+1"></Pokemon>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from './components/Pokemon';

export default {
  name: 'App',
  // Data retorna dados para serem usados no template
  data () {
    return {
      pokemons: []
    }
  },
  // Chamado sempre que o componente é carregado
  created () {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
          .then(res => {
            this.pokemons = res.data.results;
          })
          .catch(err => {
            console.log(err);
          });    
  },
  components: {
    Pokemon
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
