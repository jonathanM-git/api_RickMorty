<template>
    <router-link to="/">
        <button>Back to Episodes</button>
    </router-link>

    <h2>{{ character.name + " #" + id }}</h2>
    <div class="character-details">
        <img :src="character.image" alt="Character Image" />
        <p><b>Especies:</b> {{ character.species }}</p>
        <p><b>Género:</b> {{ character.gender }}</p>
        <p><b>Origen:</b> {{ character.origin?.name }}</p>
        <p><b>Localización:</b> {{ character.location?.name }}</p>
        <h3>Episodios</h3>
        <ul>
            <li v-for="episode in character.episode" :key="episode">
                <a :href="episode" target="_blank">{{ episode }}</a>
            </li>
        </ul>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    import { useRoute } from 'vue-router';

    const route = useRoute();
    const character = ref({});
    let id = ref(route.params.idrouter);

    fetch(`https://rickandmortyapi.com/api/character/${route.params.idrouter}`)
    .then((response) => response.json())
    .then((data) => {
        character.value = data;
    });
</script>
