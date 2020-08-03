<template>
  <div class="filmlist">
      <film-list-item v-for="(film, index) in searchedFilms" :film="film" :key="index"></film-list-item>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import FilmListItem from '@/components/FilmListItem';

export default {
    name: "film-list",
    props: ["films"],
    data() {
      return {
        searchedTerm: "",
      }
    },

    components: {
      "film-list-item": FilmListItem
    },

    computed: {
      searchedFilms () {
        return this.films.filter(film => this.filmsIncludedSearch(film));
      }
    },

    methods: {
      filmsIncludedSearch (film) {
        if (film.title.toLowerCase().includes(this.searchedTerm.toLowerCase())) {
          return true;
        } 
        return false;
    }
},

    mounted() {
      eventBus.$on('search-films', data => this.searchedTerm = data);
    }
}
</script>

<style>

</style>