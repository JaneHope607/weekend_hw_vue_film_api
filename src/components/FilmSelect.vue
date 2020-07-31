<template>
    <div class="film-select-dropdown">
    <select v-model="selectedFilm" v-on:change="handleSelect">
        <option v-for="(film, index) in films" :film="film" :key="index" v-bind:value="film">{{film.title}}</option>
    </select>
    </div>
</template>

<script>

export default {
    name: "film-select",
    data() {
        return {
            selectedFilm: null
        };
    },
    props: ["films"],
    components: {
    }
};
</script>

<style>

</style>