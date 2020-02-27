<template>
  <div class="movies-index">

    <div v-for="movie in movies">
      <h2>{{ movie.title }}</h2>
      <router-link :to="`/movies/${movie.id}`">
        <img v-bind:src="movie.image_url" alt=""><br><br>
      </router-link>
    </div>

  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      movies: []
    };
  },


  created: function() {
    axios
      .get("/api/movies")
      .then(response => {
        this.movies = response.data;
      });
  },


  methods: {}
};
</script>
