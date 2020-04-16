<template>
    <b-collapse :open="false" class="card" animation="slide" aria-id="contentIdForA11y3">
        <div
                slot="trigger"
                slot-scope="props"
                class="card-header"
                role="button"
                aria-controls="contentIdForA11y3">
            <p class="card-header-title">
                {{ game.title }}
            </p>
            <a class="card-header-icon">
                <span class="material-icons">
                    {{ props.open ? 'keyboard_arrow_up' : 'keyboard_arrow_down' }}
                </span>
            </a>
        </div>
        <div class="card-content">
            <div class="content">
                <p>{{ game.publisher }}</p>
                <a :href="game.steamUrl">Store page</a>
                <p>
                    Is fully optimized?
                    <span class="material-icons">
                        {{ game.isFullyOptimized ? 'check' : 'block' }}
                    </span>
                </p>
                <p>
                    Is highlights supported?
                    <span class="material-icons">
                        {{ game.isHighlightsSupported ? 'check' : 'block' }}
                    </span>
                </p>
            </div>
        </div>
        <footer class="card-footer">
            <p class="card-footer-item"
               v-for="genre in game.genres"
               v-bind:key="genre">
                {{ genre }}
            </p>
        </footer>
    </b-collapse>
</template>

<script>
    export default {
        name: "GameCard",
        props: {
            game: Object
        }
    }
</script>

<style scoped>
    .card {
        box-shadow: none;
        margin: 0;
    }

    .card-content {
        margin: 0;
        padding-top: 0;
        padding-bottom: 0;
    }
</style>