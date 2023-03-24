<template>
    <h1>Who is this Pokemon?</h1>
    <PokemonOptions />
    <PokemonImage />
</template>

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
