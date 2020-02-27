<template>
  <div class="movies-show">

    <h2>{{ movie.title }}</h2>
    <img v-bind:src="movie.image_url" alt="">
    <h3>Released: {{ movie.year }}</h3>
    <h4>Director: {{ movie.director }}</h4>
    <p>{{ movie.plot }}</p>

  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      movie: {}
    };
  },

  created: function() {
    axios
      .get(`/api/movies/${this.$route.params.id}`)
      .then(response => {
        console.log(response.data);
        this.movie = response.data;
      });
  },

  methods: {}
};
</script>