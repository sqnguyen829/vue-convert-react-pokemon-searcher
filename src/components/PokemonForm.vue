<template>
    <div>
        <h3>Add a Pokemon!</h3>
        <form @submit="addPokemon">
            <input fluid v-model="name" label="Name" placeholder="Name" name="name" />
            <input fluid v-model="hp" label="hp" placeholder="hp" name="hp" />
            <input fluid v-model="front" label="Front Image URL" placeholder="url" name="frontUrl" />
            <input fluid v-model="back" label="Back Image URL" placeholder="url" name="backUrl" />
          <button name="submit" type="submit">submit</button>
        </form>
      </div>
</template>

<script>
export default {
    name:'PokemonForm',
    data() {
        return{
            name:'',
            hp:'',
            front:'',
            back:''
        }
    },
    methods:{
        addPokemon(e) {
            e.preventDefault();
            console.log(parseInt(this.hp))
            const newPoke = {
                name:this.name,
                hp: typeof parseInt(this.hp) === 'number'? parseInt(this.hp) : 20 ,
                sprites:{
                    front:this.front,
                    back:this.back
                }
            }
            this.$emit('add-poke', newPoke)
            this.name = ''
            this.hp = ''
            this.front = ''
            this.back = ''
        }
    }
}
</script>