<template>
  <div v-if="film" class="wrapper">
      <div class="film details">
          <h3>Title: {{ film.title }}</h3>
           <p>Release Date: {{ film.release_date }}</p>
          <p>Description {{ film.description }}</p>
          <p>Director: {{ film.director }}</p>
          <p>Rotten Tomatoes Score: {{ film.rt_score }}</p>
      </div>  
  </div>
</template>

<script>
export default {
    name: "film-details",
    props: ["film"]
}
</script>

<style>

</style>