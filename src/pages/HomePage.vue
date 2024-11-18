<template>
    <div class="episodes-container">
        <episodeBoxComponent v-for="(episode, key) in episodeList" :name="episode?.name" :air_date="episode?.air_date" :episode="episode?.episode" :id="episode?.id" :key="key" />
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    import episodeBoxComponent from './../components/episodeBoxComponent.vue';

    const episodeList = ref([]);

    fetch("https://rickandmortyapi.com/api/episode")
        .then((response) => response.json())
        .then((data) => {
        episodeList.value = data.results;
    });
    
</script>
<style scoped lang="scss">
@import '/src/assets/HomePage.scss'; 
</style>