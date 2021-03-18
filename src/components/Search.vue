<template>
    <div class="ui search">
      <div class="ui icon input">
        <input 
        type="text" 
        @change="changeSearch" 
        v-model="inputV"/>
        <i class="search icon" />
      </div>
    </div>
</template>

<script>
export default {
    name:"Search",
    // props:["searchterm"],
    data() {
        return {
            inputV:''
        }
    },
    methods: {
        changeSearch() {
            // this.searchterm = this.inputV
            this.$emit('update-search', this.inputV)
        }
    }
}
</script>