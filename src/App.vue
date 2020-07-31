<template>
  <div>
    <h1>Films</h1>
    <div>
      <film-select :films="films"/>
    </div>
  </div>
</template>

<script>
import FilmSelect from '@/components/FilmSelect';

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
    'film-select': FilmSelect
  }
}
</script>

<style>

</style>