<template>
  <div>
    <h1>Films</h1>
    <div>
      <film-list :films="films"></film-list>
    </div>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList';

export default {
  name: 'app',
  data() {
    return {
      films: []
    };
  },

  mounted() {
      fetch('https://ghibliapi.herokuapp.com/films')
      .then(response => response.json())
      .then(data => this.films = data)
      .catch(err => console.log(err))
  },

  components: {
    'film-list': FilmList
  }
}
</script>

<style>

</style>