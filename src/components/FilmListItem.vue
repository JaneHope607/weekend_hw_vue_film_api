<template>
    <div class="filmlistitem">
        <p>{{ film.title }} - Directed by {{ film.director }}</p>
        <button v-on:click="displayInfo">More Details</button> 
    </div>
</template>

<script>
import { eventBus } from "@/main.js"

export default {
    name: "film-list-item",
    props: ["film"],
    methods: {
        displayInfo(){
            eventBus.$emit('film-select', this.film);   
        }
    }
}
</script>

<style>

</style>