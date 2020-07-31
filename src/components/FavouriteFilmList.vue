<template>
  <div class="filmlistitem">
      <p>{{ film.title }}</p>
  </div>
</template>

<script>
export default {
    name: "film-list-item",
    props: ["film"],
}
</script>

<style>

</style>