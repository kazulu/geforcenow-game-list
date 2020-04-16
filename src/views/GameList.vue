<template>
    <div>
        <b-loading :is-full-page="isFullPage" :active.sync="isLoading" :can-cancel="true"></b-loading>
        <p v-if="errorMsg">{{ errorMsg }}</p>

        <div id="game-cards" class="columns is-multiline">
            <GameCard
                    class="column is-one-third"
                    v-for="game in filteredGames"
                    v-bind:key="game.id"
                    :game="game">
            </GameCard>
        </div>
    </div>
</template>

<script>
    import GameCard from "../components/GameCard";
    import axios from 'axios';

    export default {
        name: "GameList",
        props: {
            searchText: String
        },
        components: {
            GameCard
        },
        data() {
            return {
                isFullPage: false,
                isLoading: false,
                games: [],
                errorMsg: ''
            }
        },
        computed: {
            filteredGames() {
                if (this.searchText.length == 0) {
                    return this.games;
                }

                return this.games.filter(game => {
                    const title = game.title.toLowerCase();
                    const search = this.searchText.toLowerCase();
                    return title.startsWith(search);
                });
            }
        },
        created() {
            this.isLoading = true;
            axios
                .get('https://static.nvidiagrid.net/supported-public-game-list/gfnpc.json?JSON')
                .then(response => {
                    this.games = response.data;
                    this.isLoading = false;
                })
                .catch(error => {
                    this.errorMsg = error;
                    this.isLoading = false;
                });
        }
    }
</script>

<style scoped>
    div {
        position: relative;
    }

    #game-cards {
        padding: 0 2rem;
    }
</style>