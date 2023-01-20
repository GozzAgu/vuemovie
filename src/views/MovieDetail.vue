<template>
  <div class="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <img :src="movie.Poster" class="card-img-top" alt="...">
    <h4>{{ movie.Actors }}</h4>
    <h4>{{ movie.Plot }}</h4>
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from './env';

const movie = ref({});
const route = useRoute();

onBeforeMount(() => {
  fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
  .then(response => response.json())
  .then(data => {
    movie.value = data;
    console.log(data)
  })
})
</script>

<style>

</style>