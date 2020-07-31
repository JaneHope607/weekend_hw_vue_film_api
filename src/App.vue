<template>
  <div>
    <h1>Films</h1>
    <div>
      <film-select :films="films"/>
      <film-details/>
    </div>
  </div>
</template>

<script>
import FilmSelect from '@/components/FilmSelect';
import FilmDetails from '@/components/FilmDetails';

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
    'film-select': FilmSelect,
    'film-details': FilmDetails
  }
}
</script>

<style>

</style>