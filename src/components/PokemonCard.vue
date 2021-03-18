<template>
    <div class='card' :style="{'background':'rgb(185, 185, 185)'}">
        <div @click="flipped" class="image">
            <img :src="front? pokemon.sprites.front: pokemon.sprites.back"/>
        </div>
        <div class="content">
            <div class="header">{{pokemon.name}}</div>
        </div>
        <div class="extra content">
            <span>
                <i class="icon heartbeat red" />
                {{pokemon.hp}}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name:"PokemonCard",
    props:["pokemon"],
    data() {
        return {
            front:true
        }
    },
    methods:{
        flipped() {
            this.front = !this.front
        }
    }
}
</script>