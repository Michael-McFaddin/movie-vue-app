

<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <div>
      <h2>New Movie</h2>
      <button v-on:click="createMovie">Add Movie</button>
    </div>

    <div v-for="movie in movies">
      <h2>Title: {{ movie.title }}</h2>
      <h3>Year: {{ movie.year }}</h3>
      <h3>Director: {{ movie.director }}</h3>
      <h4>Plot: {{ movie.plot }}</h4><br>
    </div>

  </div>
</template>

<style>
</style>

<script>
// var axios = require("axios");
import axios from 'axios'; //don't forget to add this!!!
export default {
  data: function() {
    return {
      message: "Mike's Movie Picks!",
      movies: []
    };
  },
  created: function() {
    axios.get("/api/movies").then(response => {
      console.log(response.data);
      this.movies = response.data;
    });
  },
  methods: {
    createMovie: function() {
      var params = {
        title: "Elf",
        year: 2003,
        plot: "Buddy (Will Ferrell) was accidentally transported to the North Pole as a toddler and raised to adulthood among Santa's elves. Unable to shake the feeling that he doesn't fit in, the adult Buddy travels to New York, in full elf uniform, in search of his real father. As it happens, this is Walter Hobbs (James Caan), a cynical businessman. After a DNA test proves this, Walter reluctantly attempts to start a relationship with the childlike Buddy with increasingly chaotic results.",
        director: "Jon Favreau",
        english: true,
      };
      axios.post("/api/movies", params)
        .then(response => {
          console.log("Success!", response.data);
          this.movies.push(response.data);
        })
        .catch(error => {
          console.log(error.response.data.errors);
        });
    }
  }
};
</script>

