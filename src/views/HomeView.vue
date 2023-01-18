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

    <div class="movies-list">
      <h1>Movies</h1>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const search = ref('');

const searchMovies = () => {
  if(search.value !== '') {
    console.log(search.value)
  }
}
</script>
