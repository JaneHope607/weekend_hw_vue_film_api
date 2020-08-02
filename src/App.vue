<template>
  <div id="app">
    <h1>Studio Ghibli Films</h1>
    <search-films></search-films>
    <div class="list-info">
      <film-list :films="films"></film-list>
      <film-details v-if="selectedFilm" :film="selectedFilm"></film-details>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js';

import FilmList from './components/FilmList';
import FilmDetails from './components/FilmDetails';
import FilmSearch from './components/FilmSearch.vue';

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },

  mounted() {
      fetch('https://ghibliapi.herokuapp.com/films')
      .then(response => response.json())
      .then(data => this.films = data)
      .catch(err => console.log(err));

      eventBus.$on('film-select', (film) => {
        this.selectedFilm = film
      });

  },

  components: {
    'film-list': FilmList,
    'film-details': FilmDetails,
    'search-films': FilmSearch
  }
}
</script>

<style lang="css" scoped>

.list-info {
  display: inline-flex;
  background-color: rgb(204, 196, 147);
}

#app {
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
</style>