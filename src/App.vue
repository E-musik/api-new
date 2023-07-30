<template>
  <h1>Movie API</h1>

  <div class="Results">
    <h1>Results</h1>
        
    <div v-if="loading">loading...</div>
    <div v-else-if="movieData">
      <h2>{{ movieData.Title }}</h2>
      <p>Year: {{ movieData.Year }}</p>
      <p>Plot: {{ movieData.Plot }}</p>
      <p>Genre: {{ movieData.Genre }}</p>
      <p>Language: {{ movieData.Language }}</p>
      <p>Country: {{ movieData.Country }}</p>
      <p>Awards: {{ movieData.Awards }}</p>
      <p>Poster: {{ movieData.Poster }}</p>
      <p>Ratings: {{ movieData.Ratings }}</p>
      <p>Type: {{ movieData.Type }}</p>
      <p>BoxOffice {{ movieData.BoxOffice }}</p>
      <p>Production: {{ movieData.Production }}</p>
    </div>
    <div v-else> No movie data</div>
      
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const apiKey = '96b56e3b'; 
const movieId = 'tt3896198'; 

const loading = ref(true); 
const movieData = ref(null); 

onMounted(async () => { 
  try { 
    const response = await axios.get(`http://www.omdbapi.com/?i=${movieId}&apikey=${apiKey}`); 
    movieData.value = response.data; 
    loading.value = false; 
  } 
  catch (error) { 
    console.error('Error fetching movie data:', error); 
    loading.value = false; 
  } 
});
</script>

<style>
  
</style>
