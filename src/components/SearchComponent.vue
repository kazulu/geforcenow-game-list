<template>
    <div>
        <input
                class="input"
                type="text"
                placeholder="Call of Cthulhu"
                v-on:keyup="$emit('updateSearchText', searchText)"
                v-model="searchText">
    </div>
</template>

<script>
    export default {
        name: "SearchComponent",
        data() {
            return {
                searchText: ''
            }
        }
    }
</script>

<style scoped>
    input {
        width: 50%;
    }
</style>