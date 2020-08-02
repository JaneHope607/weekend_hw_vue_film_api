<template>
        <div class="search-bar">
            <input type="text" id="search-bar-input" v-model="searchQuery" placeholder="Search film by title..." v-on:input="handleInput"/>
        </div>
</template>

<script>
import { eventBus } from '../main.js'; 

export default {
    name: "search-films",
    data() {
        return {
            searchQuery: ""
        }
    },
    props: ["films"],

    mounted() {
        this.handleInput();
    },

    methods: {
        handleInput() {
            eventBus.$emit('search-films', this.searchQuery);
        },
    },
};
</script>

<style>

.search-bar {
    margin: 15px;
}

input {
    padding: 10px;
    width: 250px;
    border: 2px solid grey;
    border-radius: 5px;
}

</style>