<template>
  <div class="movies-edit">

    <div class="container">
      <form v-on:submit.prevent="updateMovie(movie)">
        <h1>Edit Movie</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Title:</label> 
          <input type="text" class="form-control" v-model="movie.title">
        </div>
        <div class="form-group">
          <label>Year:</label>
          <input type="text" class="form-control" v-model="movie.year">
        </div>
        <div class="form-group">
          <label>Director:</label>
          <input type="text" class="form-control" v-model="movie.director">
        </div>
        <div class="form-group">
          <label>Plot:</label>
          <textarea type="text" class="form-control" v-model="movie.plot">
        </textarea>
        </div>
        <div class="form-group">
          <label>Box Cover URL:</label>
          <input type="text" class="form-control" v-model="movie.image_url">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>

      <div>
        <button v-on:click="destroyMovie()">Delete Movie</button>
      </div>

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
      movie: {},
      errors: []
    };
  },


  created: function() {
    axios
      .get(`/api/movies/${this.$route.params.id}`)
      .then(response => {
        this.movie = response.data;
      });
  },


  methods: {
    updateMovie: function(movie) {
      var params = {
        title: movie.title,
        year: movie.year,
        director: movie.director,
        plot: movie.plot,
        image_url: movie.image_url
      };
      axios
        .patch(`/api/movies/${this.movie.id}`, params)
        .then(response => {
          this.$router.push(`/movies/${this.movie.id}`);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    },
    destroyMovie: function() {
      axios
        .delete(`/api/movies/${this.movie.id}`)
        .then(response => {
          this.$router.push("/movies");
        });
    }
  }
};
</script>
