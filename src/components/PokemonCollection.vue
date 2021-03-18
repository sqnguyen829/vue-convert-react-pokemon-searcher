<template>
    <b-container>
        <b-row cols="6">
            <PokemonCard :key="pokemon.id" :pokemon="pokemon" v-for="pokemon in pokemons"/>
        </b-row>
    </b-container>
</template>

<script>
import PokemonCard from './PokemonCard'

export default {
    name:'PokemonCollection',
    props:["pokemons"],
    components:{
        PokemonCard
    }
}
</script>