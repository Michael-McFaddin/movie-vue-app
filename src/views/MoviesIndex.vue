<template>
  <div class="movies-index">
    
    <!-- Start Movies Index  -->
    <div class="categories-shop">
        <div class="container">
            <div v-for="movie in movies" class="row" v-on:click="selectedMovie = movie" v-bind:class="{selected: movie === selectedMovie}">
                <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12">
                    <div class="shop-cat-box">
                        <img class="img-fluid" v-bind:src="movie.image_url" alt="" />
                        <router-link class="btn hvr-hover" :to="`/movies/${movie.id}`">{{ movie.title }}</router-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- End Movies Index -->

  </div>
</template>


<style>
.selected {
  background-color: grey;
  transition: background-color 1s ease;
}
</style>


<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      movies: [],
      selectedMovie: {}
    };
  },


  created: function() {
    axios
      .get("/api/movies")
      .then(response => {
        this.movies = response.data;
        console.log(response.data);
      });
  },


  methods: {}
};
</script>
