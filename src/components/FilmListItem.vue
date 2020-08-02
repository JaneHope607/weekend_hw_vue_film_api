<template>
    <div class="filmlistitem">
        <p>{{ film.title }} - Directed by {{ film.director }}</p>
        <button v-on:click="displayInfo">More Details</button> 
    </div>
</template>

<script>
import { eventBus } from "../main.js"

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

<style scoped>
    .filmlistitem {
        display: flex;
        flex-direction: column;
        padding: 20px;
        align-items: center;
        width: 150px;
        border-radius: 20px;
        background-color: white;
        text-align: center;
        margin: 10px;

    }
    button {
        list-style: none;
        margin: 10px;
        text-decoration: none;
        background-color: #333333;
        color: white;
        padding: 2px 6px 2px 6px;
    }

</style>