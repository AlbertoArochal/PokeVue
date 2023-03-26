<template>
    <h1 v-if="!pokemon">Loading Pokemon...</h1>
    <div v-else class="Pokemon-container">
        <h1>Who is this Pokemon?</h1>
        <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon" />
        <PokemonOptions :pokemons="pokemonArr" />
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
            showPokemon: true,
        };
    },
    methods: {
        async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions();
            const rndInt = Math.floor(Math.random() * 4);
            this.pokemon = this.pokemonArr[rndInt];
        },
    },
    mounted() {
        this.mixPokemonArray();
    },
};
</script>
