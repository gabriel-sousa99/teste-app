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
    <h1 id="titulo">{{ titulo }}</h1>
  </div>
  <div class="pagina-inicial row justify-center">
    <button @click="titulo = 'alterado'">Mudar o texto</button>
    <button @click="titulo = 'mudou o valor'">Mudar o texto 2</button>
    <button @click="titulo = 'Pokédex'">Voltar ao valor inicial</button>
  </div>
</template>

<style scoped>
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

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MainLayout",

  setup() {
    return {
      titulo: ref("Pokédex"),
    };
  },
});
</script>
