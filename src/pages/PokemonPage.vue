<template>
    <h1 v-if="!pokemon">Loading Pokemon...</h1>
    <div v-else class="Pokemon-container">
        <h1>Who dis?</h1>
        <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon" />
        <PokemonOptions
            :pokemons="pokemonArr"
            @selection="checkAnswer($event)"
        />
        <template v-if="showPokemon">
            <h2>{{ message }}</h2>
            <button @click="newGame" class="fade-in">New Game</button></template
        >
    </div>
</template>

<script>
import PokemonOptions from "@/components/PokemonOptions.vue";
import PokemonImage from "@/components/PokemonImage.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";
export default {
    name: "PokemonPage",

    components: {
        PokemonOptions,
        PokemonImage,
    },
    data: function () {
        return {
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
            showAnswer: false,
            message: "",
        };
    },
    methods: {
        async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions();
            const rndInt = Math.floor(Math.random() * 4);
            this.pokemon = this.pokemonArr[rndInt];
        },
        checkAnswer(selectedId) {
            this.showPokemon = true;
            if (selectedId === this.pokemon.id) {
                this.message = "Correct!";
            } else {
                this.message = `Wrong! the correct answer is: ${this.pokemon.name}`;
            }
        },
        newGame() {
            this.showPokemon = false;
            this.message = "";
            this.mixPokemonArray();
            this.pokemon = null;
            this.pokemonArr = [];
        },
    },
    mounted() {
        this.mixPokemonArray();
    },
};
</script>
