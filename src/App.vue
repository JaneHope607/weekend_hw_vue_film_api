<template>
  <div>
    <h1>Films</h1>
    <div>
      <film-select :films="films"></film-select>
      <film-details :film="selectedFilm"></film-details>
    </div>
  </div>
</template>

<script>
import FilmSelect from '@/components/FilmSelect';
import FilmDetails from '@/components/FilmDetails';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    };
  },

  mounted() {
      fetch('https://ghibliapi.herokuapp.com/films')
      .then(response => response.json())
      .then(data => this.films = data)
      .catch(err => console.log(err));

      eventBus.$on('film-select', (film) => {
        this.selectedFilm = film;
      });
  },

  components: {
    'film-select': FilmSelect,
    'film-details': FilmDetails
  }
}
</script>

<style>

</style>