<template>
  <div class="home">
    <form @submit.prevent="searchMovies()" class="search">
      <input type="text" v-model="Search" placeholder="What are you looking for?" />
      <input type="submit" value="search" />
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
      <div class="columns is-desktop">
        <div class="column">{{ movie.Title }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import env from './env';

const Search = ref('');
const movies = ref(['']);

const searchMovies = () => {
  if(Search.value !== '') {
    fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${Search.value}`)
    .then(response => response.json())
    .then(data => {
      movies.value = data.Search;
      Search.value = '';
      console.log(data)
    })
  }
}
</script>
