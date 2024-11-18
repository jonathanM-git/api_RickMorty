<template>
    <div class="episode-box-item">
        <router-link :to="{ name: 'SingleEpisodePage', params: { idrouter: id }}">
            <div class="episode-details">
            <h3>{{ name }}</h3>
            <p><b>Fehca de emisión:</b> {{ air_date }}</p>
            <p><b>Episodio:</b> {{ episode }}</p>
            </div>
        </router-link>
    </div>
</template>

<script setup>
    const props = defineProps({
        name: String,
        air_date: String,
        episode: String,
        id: Number,
    });
</script>
