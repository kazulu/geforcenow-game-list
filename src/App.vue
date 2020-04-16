<template>
    <div id="app">
        <h1 class="title is-1">Nvidia GeForce Game List</h1>
        <h2 class="subtitle">
            Source
            <a href="https://static.nvidiagrid.net/supported-public-game-list/gfnpc.json?JSON">
                https://static.nvidiagrid.net/supported-public-game-list/gfnpc.json?JSON
            </a>
        </h2>
        <SearchComponent v-on:updateSearchText="searchText = $event"></SearchComponent>
        <GameList :searchText="searchText"></GameList>
    </div>
</template>

<script>
    import SearchComponent from "./components/SearchComponent";
    import GameList from "./views/GameList";

    export default {
        components: {
            SearchComponent,
            GameList
        },
        data() {
            return {
                searchText: ''
            }
        }
    }
</script>

<style>
    div {
        text-align: center;
        margin: 2rem 0;
    }
</style>