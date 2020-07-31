<template>
    <div class="film-list">
        <film-list-item v-for="(fim, index) in films" :film="film" :key="index"></film-list-item>
    </div>
</template>

<script>
export default {
    name: "film-list",
    props: ["films"],
    components: {
        "film-list-item": FimListItem
    }
};
</script>

<style>

</style>