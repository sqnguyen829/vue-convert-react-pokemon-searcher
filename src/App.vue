<template>
  <div class="App" :style="{'background':'rgb(226, 224, 224)'}">
    <PokemonPage :pokemons="pokemons"/>
  </div>
</template>

<script>
import PokemonPage from './components/PokemonPage'

export default {
  name: 'App',
  components: {
    PokemonPage
  },
  data() {
    return{
      pokemons:[],
      searchterm:''
    }
  },
  created() {
    fetch('http://localhost:3000/pokemon', {
      method:'GET'
    })
    .then(res => res.json())
    .then(data => this.pokemons = data)
    .catch(err => console.log(err))
  }
}
</script>

<style>

.App {
  text-align: center;
}

.App-logo {
  animation: App-logo-spin infinite 20s linear;
  height: 80px;
}

.App-header {
  background-color: #222;
  height: 150px;
  padding: 20px;
  color: white;
}

.App-title {
  font-size: 1.5em;
}

.App-intro {
  font-size: large;
}

</style>
