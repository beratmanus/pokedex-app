<template>
    <h5 class="text-left m-4 text-white font-bold">INFO</h5>
    <div class="m-3 border-2 border-black-200 rounded-xl bg-white">
    <div class="flex m-4 justify-evenly">
        <div class="text-gray-400 text-left m-1 float-left w-full">
            <p>Type</p>
            <p>Number</p>
            <p>Weight</p>
            <p>Height</p>
            <p>Abilities</p>
        </div>
        <div class="float-left w-full m-1 text-left">
            <div class="flex mb-4">
                <div v-for="type in pokemon.types" :key="pokemon.name + type.type.name">
                    <p class="type" :id="type.type.name">{{type.type.name}}</p>
                </div>
            </div>
            <p>{{pokemon.id}}</p>
            <p>{{pokemon.weight / 10}}kg</p>
            <p>{{pokemon.height / 10}}m</p>
            <div v-for="ability in pokemon.abilities" :key="pokemon.name + ability.ability.name">
                    <p class="mb-1" :id="ability.ability.name">{{ability.ability.name}}</p>
            </div>
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
  }
  
}
</script>

<style scoped>
.type {
    color: white;
    border-radius: 50px;
    margin: 0 0.2em;
    padding: 0.1em 0.7em;
    width: fit-content;
    text-align: center;
    font-size: 0.8em;
} 
p{
    margin-bottom: 16px;
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