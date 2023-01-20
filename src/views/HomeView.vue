<template>
  <div class="home">
    <form @submit.prevent="searchMovies()" class="search">
      <div class="input-group mb-3 p-5">
        <input class="form-control" type="text" v-model="Search" placeholder="What are you looking for?">
        <button class="btn btn-outline-secondary" type="submit" id="button-addon1" value="search">Button</button>
      </div>
    </form>

    <div class="feature-card p-5">
      
    </div>

    <div class="movie-list ps-5 pe-5" v-for="movie in movies" :key="movie.imdbID">
      <div class="cards p-2">
        <div class="card" style="width: 18rem;">
          <img :src="movie.Poster" class="card-img-top" alt="...">
          <div class="card-body">
            <router-link :to="`/movie/${movie.imdbID}`">
              {{ movie.Title }}
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import env from './env';

const Search = ref('');
const movies = ref([]);

const searchMovies = () => {
  if(Search.value !== '') {
    fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${Search.value}`)
    .then(response => response.json())
    .then(data => {
      movies.value = data.Search;
      Search.value = '';
      movies.value.push(data)
      console.log(data)
    })
  }
}
</script>

<style scoped>

</style>