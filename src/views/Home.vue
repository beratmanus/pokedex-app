<template>
  <div class="home">
    <div v-for="pokemon in pokemons" :key="pokemon.id">
      <h2>{{pokemon.name}}</h2>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
// list op pokemon api : https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon
//details api: https://pokeapi.co/api/v2/pokemon/133  


export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      pokemons: []
    }
  },
  mounted() {
    fetch('https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon')
    .then(res => res.json())
    .then(data => this.pokemons = data)
    .then(console.log(this.pokemons))
  },
}
</script>
