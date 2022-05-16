<template>
  <div class="home">
    <div class="mx-4 mb-4 flex justify-end">

    <button
      type="button"
      @click="showModal"
      class="m-2"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4" />
      </svg>
    </button>
    </div>

    <Modals
      v-show="isModalVisible"
      @close="closeModal"
    />
    <h1 class="font-bold text-left pl-4 text-3xl">Pokédex</h1>
    
      <PokemonList />
  </div>
      
</template>

<script>
// @ is an alias to /src
//details api: https://pokeapi.co/api/v2/pokemon/133  
  import Modals from '../components/Modals.vue';
  import PokemonList from '../components/PokemonList.vue';
const listPokemonUrl = "https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon"

export default {
  name: 'Home',
  components: {
    Modals,
    PokemonList,
  },
  data() {
    return {
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
  }

</script>
<style scoped>
  p{
    font-size: 12px;
  }
  .home{
    background: #F9F9F9;
  }
  
  input[type="text"]{
    padding-left: 35px;
    text-align: left;
  }
</style>
