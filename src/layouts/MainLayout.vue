<template>
  <div class="navbar">
    <div class="linha">
      Pokédex<img
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Pok%C3%A9_Ball_icon.svg/1200px-Pok%C3%A9_Ball_icon.svg.png"
        alt=""
        style="width: 50px; height: 50px"
      />
    </div>
  </div>

  <div class="pagina-inicial row justify-center">
    <div class="cartao" v-for="pokemon in resultado" :key="pokemon?.name">
      <p>{{ pokemon?.name.toUpperCase() }}</p>
      <img :src="pokemon.imagem" alt="" style="height: 150px" />
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";

const url = "https://pokeapi.co/api/v2/pokemon/?offset=0&limit=10";

export default defineComponent({
  name: "MainLayout",
  setup() {
    return {
      resultado: ref([]),
    };
  },
  methods: {
    async pegarPokemon() {
      const resposta = await fetch(url);
      const dados = await resposta.json();
      this.resultado = dados.results;
      for (const pokemon of this.resultado) {
        const resposta = await fetch(pokemon.url);
        const dados = await resposta.json();
        pokemon.imagem = dados.sprites.other["official-artwork"].front_default;
      }
    },
  },
  async mounted() {
    await this.pegarPokemon();
  },
});
</script>

<style scoped>
.cartao {
  background-color: #f44336;
  color: white;
  padding: 10px;
  font-size: 20px;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  margin: 20px;
  justify-content: center;
  border-radius: 10px;
  box-shadow: black 0px 0px 10px;
  align-items: center;
}
.cartao a {
  text-decoration: none;
  color: white;
  text-align: center;
}
.navbar {
  background-color: #f44336;
  color: white;
  padding: 10px;
  font-size: 20px;
  font-weight: bold;
  display: flex;
  justify-content: flex-end;
}
.linha {
  display: flex;
  flex-direction: row;
  align-items: center;
}
</style>
