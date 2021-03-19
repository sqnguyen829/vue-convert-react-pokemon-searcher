<template>
  <div class="App" :style="{'background':'rgb(226, 224, 224)'}">
    <h1>Pokemon Searcher</h1>
    <br />
    <PokemonForm v-on:add-poke="addPoke"/>
    <br />
    <Search v-on:update-search="updateSearch"/>
    <br />
    <PokemonPage 
      :pokemons="pokemons | searchFilter(searchterm)"
      :searchterm="searchterm"
      v-on:search="updateSearch"
      v-on:add-poke="addPoke"
      />
  </div>
</template>

<script>
import PokemonPage from './components/PokemonPage'
import Search from './components/Search'
import PokemonForm from './components/PokemonForm'

export default {
  name: 'App',
  components: {
    PokemonPage,
    Search,
    PokemonForm
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
    .then(data => {
      this.pokemons = data
      })
    .catch(err => console.log(err))
  },
  methods:{
    updateSearch(stuff) {
      console.log(stuff)
      this.searchterm = stuff
    },
    addPoke(poke) {
      console.log(poke)
      fetch('http://localhost:3000/pokemon', {
        method:'POST',
        headers:{
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(poke)
      })
      .then(res => res.json())
      .then(data => this.pokemons = [...this.pokemons, data])
      .catch(err => console.log(err))
    }
  },
  filters: {
    searchFilter: function(arr,term) {
      let newPokeList = arr.filter(pokemon => pokemon.name.toLowerCase().includes(term.toLowerCase()))
      return newPokeList
    }

    //this works
    // searchFilter(arr,term) {
    //   let newPokeList = arr.filter(pokemon => pokemon.name.toLowerCase().includes(term.toLowerCase()))
    //   return newPokeList
    // }

    //this works
    // searchFilter: (arr,term) => {
    //   let newPokeList = arr.filter(pokemon => pokemon.name.toLowerCase().includes(term.toLowerCase()))
    //   return newPokeList
    // }

    //This doesn't work 'this' doesn't work here
    // searchFilter: (arr) => {
    //   let newPokeList = arr.filter(pokemon => pokemon.name.toLowerCase().includes(this.searchterm.toLowerCase()))
    //   return newPokeList
    // }
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
