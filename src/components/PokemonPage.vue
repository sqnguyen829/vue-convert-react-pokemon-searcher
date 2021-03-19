<template>
    <div>
        <!-- <Container> -->
            <!-- <h1>Pokemon Searcher</h1>
            <br />
            <PokemonForm v-on:add-poke="$emit('add-poke', poke)"/>
            <br /> -->
            <!-- <Search v-on:update-search="$emit('update-search')"/> -->
            <br />
            <PokemonCollection :pokemons="pokemons"/>
        <!-- </Container> -->
    </div>
</template>

<script>
// import PokemonForm from './PokemonForm'
// import Search from './Search'
import PokemonCollection from './PokemonCollection'

export default {
    name:'PokemonPage',
    props:["pokemons"],
    components:{
        // PokemonForm,
        // Search,
        PokemonCollection
    }
}
</script>