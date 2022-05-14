<template>
  <div class="home">
    <button
      type="button"
      class="btn"
      @click="showModal"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
  <path stroke-linecap="round" stroke-linejoin="round" d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4" />
</svg>
    </button>

    <Modals
      v-show="isModalVisible"
      @close="closeModal"
    />
    <h1 class="font-bold text-left pl-4 text-3xl">Pokedex</h1>
    <div class="flex m-2 relative">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 absolute m-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
  <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
</svg>
    <input :disabled="searchDisable" type="text" placeholder="Pokemon zoeken" class="border-2 p-2 text-center rounded-xl w-full" v-model="filterPokemon">  
    </div>
    <div class="drop-shadow-2xl" v-for="pokemon in filteredItems" :key="pokemon.id" >
        <router-link class="flex p-2 m-3 pokedex  rounded-xl justify-between capitalize" :to="{ name: 'Details', params: { id: pokemon.id, name: pokemon.name, img: pokemon.sprites.front_default} }">
      <div class="flex">
        <img :src=pokemon.sprites.front_default alt="" class="">
      <div class="flex-col m-2">
          <h2 class="text-left">{{pokemon.name}}</h2>
          <p class="text-left">Nr. {{pokemon.id}}</p>
        </div> 
      </div>
      <div class="flex">
          <p class="text-right border-2 m-1 rounded-xl h-8 py-1 px-3">{{pokemon.types[0].type.name}}</p>
          <p class="text-center border-2 m-1 rounded-xl h-8 py-1 px-3" v-if="pokemon.types.length > 1">{{pokemon.types[1].type.name}}</p>
          <p class="m-2">></p>
      </div>
        </router-link>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
//details api: https://pokeapi.co/api/v2/pokemon/133  
  import Modals from '../components/Modals.vue';

const listPokemonUrl = "https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon"

export default {
  name: 'Home',
  components: {
    Modals
  },
  data() {
    return {
      pokemons: [],
      filterPokemon: '',
      isModalVisible: false,
      searchDisable: false,

    }
  },
  methods: {
      showModal() {
        this.isModalVisible = true;
        this.searchDisable = true;
      },
      closeModal() {
        this.isModalVisible = false;
        this.searchDisable = false;
      }
    },
  mounted() {
    fetch(listPokemonUrl)
    .then(res => res.json())
    .then(data => this.pokemons = data)
  },
   computed: {
    filteredItems() {
      return this.pokemons.filter((pokemon) => {
        return pokemon.name.toLowerCase().includes(this.filterPokemon.toLowerCase()) || String(pokemon.id).includes(this.filterPokemon);
      });
    },
    },
  }

</script>
<style>
  img{
    height: 70px;
    width: 70px;
  }

  p{
    font-size: 12px;
  }
  .home{
    background: #F9F9F9;
  }
  .pokedex{
    background: #FFFFFF;
  }
  input[type="text"]{
    padding-left: 35px;
    text-align: left;
    
  }
</style>
