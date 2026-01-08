<template>
    <div v-if="pokemon && pokemonOptions.length > 0">
        <h1>¿Quién es este Pokémon?</h1>
        <PokemonImage :imageUrl="imageUrl" />
        <PokemonOpciones :options="pokemonOptions" :correctAnswer="pokemon.name" @answered="handleAnswer" />
        <div v-if="message" :class="['message', messageClass]">
            {{ message }}
        </div>
    </div>
    <div v-else>
        <p>Cargando...</p>
    </div>
</template>

<script>
import PokemonImage from '../components/pokemonImage.vue';
import PokemonOpciones from '../components/pokemonOpciones.vue';
import { obtenerPokemons, obtenerImagen } from '../clients/pokemonClient';

export default {
    components: {
        PokemonImage,
        PokemonOpciones,
    },
    data() {
        return {
            pokemon: null,
            imageUrl: null,
            pokemonOptions: [],
            message: '',
            messageClass: ''
        }
    },
    mounted() {
        this.cargarJuego();
    },
    methods: {
        async cargarJuego() {
            try {
                // Obtener 4 pokemons aleatorios
                const pokemons = await obtenerPokemons();
                this.pokemonList = pokemons;
                this.pokemonOptions = pokemons.map(p => p.name);

                // Seleccionar uno de los 4 como el correcto
                const randomIndex = Math.floor(Math.random() * 4);
                this.pokemon = pokemons[randomIndex];

                // Obtener la imagen del pokemon seleccionado
                this.imageUrl = await obtenerImagen(this.pokemon.id);
            } catch (error) {
                console.error('Error al cargar el juego:', error);
            }
        },
        handleAnswer(isCorrect) {
            if (isCorrect) {
                this.message = '¡Correcto!';
                this.messageClass = 'correct';
            } else {
                this.message = `Incorrecto. Era ${this.pokemon.name}`;
                this.messageClass = 'incorrect';
            }
            setTimeout(() => {
                this.message = '';
                this.pokemon = null;
                this.imageUrl = null;
                this.pokemonOptions = [];
                this.cargarJuego();
            }, 2000);
        }
    }
}
</script>

<style>
h1 {
    text-align: center;
    text-transform: capitalize;
    font-size: 2em;
    margin: 20px 0;
}

.message {
    text-align: center;
    font-size: 1.5em;
    font-weight: bold;
    margin: 20px 0;
    padding: 10px;
    border-radius: 5px;
}

.correct {
    background-color: #4caf50;
    color: white;
}

.incorrect {
    background-color: #f44336;
    color: white;
}
</style>