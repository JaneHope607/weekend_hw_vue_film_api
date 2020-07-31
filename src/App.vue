<template>
  
</template>

<script>
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
  }
}
</script>

<style>

</style>