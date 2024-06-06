<script setup>
import { ref } from 'vue'

const pokemons = ref([])
function loadPokemons() {
    fetch('https://pokeapi.co/api/v2/pokemon')
        .then(function (response) {
            return response.json()
        })
        .then(function (data) {
            // console.log(data.results)
            for (let i = 0; i < data.results.length; i++) {
                pokemons.value.push(data.results[i])
            }
        });
}
</script>
<template>
    <div class="bg-slate-300 mb-1" v-for="(pok, index) in pokemons" :key="index">
        {{ pok.name }}
    </div>

    <button @click="loadPokemons">Cargar Pokemon</button>
</template>