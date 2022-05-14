<template>
    <h5 class="text-left m-4">STATISTIEKEN</h5>
<div class="m-3 border-2 border-black-200 rounded-xl">
 
    <div class="flex m-4 justify-evenly">
        <div class="text-gray-400 text-left m-1 float-left w-full">
            <p>HP</p>
            <p>Attack</p>
            <p>Defense</p>
            <p>Sp. Atk</p>
            <p>Sp. Def</p>
            <p>Speed</p>
            <p>Total</p>
        </div>
        <div class="flex-column w-full text-left">
            <div v-for="stat in pokemon.stats" :key="pokemon.name + stat.stat.name">
                <p>{{stat.base_stat}}</p>
            </div>
                <p>90</p>
        </div>
    </div>
  </div>
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
  computed: {
       
  }
}
</script>

<style>
    p{
    margin-bottom: 16px;
}
</style>