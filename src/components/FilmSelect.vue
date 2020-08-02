<template>
    <div class="film-select-dropdown">
    <select v-model="selectedFilm" v-on:change="handleSelect">
        <option disabled="">Choose A Film</option>
        <option v-for="(film, index) in films" :film="film" :key="index" v-bind:value="film">{{film.title}}</option>
    </select>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "film-select",
    data() {
        return {
            selectedFilm: null
        };
    },
    props: ["films"],
    components: {
    },
    methods: {
        handleSelect() {
            eventBus.$emit('film-selected', this.selectedFilm)        }
    }
};
</script>

<style>

</style>