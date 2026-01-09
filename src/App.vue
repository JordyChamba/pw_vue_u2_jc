<template>
  <div>
    <button @click="destruir" class="btn-destruir">
      {{ mostrar ? 'Destruir Componente' : 'Mostrar Componente' }}
    </button>

    <!--contadorView /-->
    <!--DirectivasView /-->
    <PokemonView v-if="mostrar" />
  </div>
</template>

<script>
//import contadorView from './views/contadorView.vue';
//import DirectivasView from './views/DirectivasView.vue';
import PokemonView from './views/pokemonView.vue';
export default {
  components: {
    PokemonView,
  },
  data() {
    return {
      mostrar: true
    }
  },
  methods: {
    destruir() {
      this.mostrar = !this.mostrar;
    }
  }
}
</script>

<style>
.btn-destruir {
  background-color: #f44336;
  color: white;
  padding: 15px 30px;
  font-size: 1.2em;
  font-weight: bold;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin: 20px;
  transition: all 0.3s ease;
}

.btn-destruir:hover {
  background-color: #d32f2f;
  transform: scale(1.05);
}
</style>