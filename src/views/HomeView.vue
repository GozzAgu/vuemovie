<template>
  <div class="home">
    <form @submit.prevent="searchMovies()" class="search">
      <input type="text" v-model="search" placeholder="What are you looking for?" />
      <input type="submit" value="Search" />
    </form>

    <div class="feature-card">
      <router-link to="/movie/Naruto">
        <img src="" />
        <div class="detail">
          <h3>Naruto</h3>
        </div>
      </router-link>
    </div>

    <div class="movie-list" v-for="movie in movies" :key="movie.imdbID">
      <h2>{{ movie }}</h2>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import env from './env';

const search = ref('');
const movies = ref(['']);

const searchMovies = () => {
  if(search.value !== '') {
    fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
    .then(response => response.json())
    .then(data => {
      movies.value = data.search;
      search.value = '';
      console.log(data)
    })
  }
}
</script>
