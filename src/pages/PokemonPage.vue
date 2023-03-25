<template>
    <h1>Who is this Pokemon?</h1>
    <PokemonImage :pokemonId="4" :showPokemon="true" />
    <PokemonOptions />
</template>
import PokemonOptions from "@/components/helpers/PokemonOptions.vue";
<script>
import PokemonOptions from "@/components/PokemonOptions.vue";
import PokemonImage from "@/components/PokemonImage.vue";
export default {
    name: "PokemonPage",

    components: {
        PokemonOptions,
        PokemonImage,
    },
};
</script>
