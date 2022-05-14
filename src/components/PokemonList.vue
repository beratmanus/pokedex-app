<template>
  <div class="flex m-2 relative">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 absolute m-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
      </svg>
    <input  type="text" placeholder="Pokemon zoeken" class="border-2 p-2 text-center rounded-xl w-full" v-model="filterPokemon">  
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
        <div class="m-0 float-right" v-for="type in pokemon.types" :key="pokemon.name + type.type.name">
                <span class="type" :id="type.type.name">{{type.type.name}}</span>
            </div>
          <!-- <p class="text-right border-2 m-1 rounded-xl h-8 py-1 px-3">{{pokemon.types[0].type.name}}</p>
          <p class="text-center border-2 m-1 rounded-xl h-8 py-1 px-3" v-if="pokemon.types.length > 1">{{pokemon.types[1].type.name}}</p>
          <p class="m-2">></p> -->
      </div>
        </router-link>
    </div>
    
  
</template>

<script>
// @ is an alias to /src
//details api: https://pokeapi.co/api/v2/pokemon/133  
  

const listPokemonUrl = "https://stoplight.io/mocks/appwise-be/pokemon/57519009/pokemon"

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      pokemons: [],
      filterPokemon: '',
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
        return pokemon.name.toLowerCase().includes(this.filterPokemon.toLowerCase()) || String(pokemon.id).match(this.filterPokemon);
      });
    },
    },
  }

</script>

<style scoped>
  img{
    height: 70px;
    width: 70px;
  }
  .pokedex{
    background: #FFFFFF;
  }
  .type {
    color: white;
    border-radius: 50px;
    margin: 0 0.2em;
    padding: 0.1em 0.7em;
    width: fit-content;
    text-align: center;
    font-size: 0.8em;
}
#grass {
    background-color: #95C24D;
}
#poison {
    background-color: #BA7EC8;
}
#fire {
    background-color: #FD7D25;
}
#water {
    background-color: #4592C3;
}
#electric {
    background-color: #FFCF00;
}
#ground {
    background-color: #D5B35B;
}
#fighting {
    background-color: #A23B6C;
}
#psychic {
    background-color: #F85888;
}
#rock {
    background-color: #B6A136;
}
#ice {
    background-color: #36e1ff;
}
#ghost {
    background-color: #7B62A3;
}
#normal {
    background-color: #A3ACAE;
}
#flying {
    background-color: #6ab2de;
}
#bug {
    background-color: #6d9036;
}
#fairy {
    background-color: #F8D4F3;
}
#dragon {
    background-color: #8B4513;
}
#steel {
    background-color: #303030;
}
</style>