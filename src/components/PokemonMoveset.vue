<template>

    <h5>MOVESET</h5>
    <p>
        
    </p>
</template>

<script>
export default {
  props: ['id' , 'name' , 'img'],
  data() {
    return {
      pokemon: [],
      
    }
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon/' + this.$route.params.id)
    .then(res => res.json())
    .then(data => this.pokemon = data)
  },
  
  
}
</script>

<style>

</style>