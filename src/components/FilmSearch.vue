<template>
    <div class="search-bar">
        <input type="text" v-model="searchQuery" placeholder="Search film by title..." v-on:keyup="searchForFilm" >
    </div>
</template>

<script>
import { eventBus } from '@/main.js'; 

export default {
    name: "search-films",
    data() {
        return {
            searchQuery: "",
            selectedFilm: {}
        };
    },
    props: ['films'],
    
    mounted() {
        this.searchForFilm();
    },

    methods: {
        searchForFilm() {
            let foundFilm = this.films.find((film) => {
                return film.title.toLowerCase().indexOf(this.searchQuery.toLowerCase()) > -1
            })
            this.selectedFilm = foundFilm

            eventBus.$emit('film-selected', this.selectedFilm)
        }
    }
}
</script>

<style>

</style>