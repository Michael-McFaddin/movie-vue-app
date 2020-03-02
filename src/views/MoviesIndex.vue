<templƒate>
  <div class="movies-index">
    
    <!-- bootstrap cards for each movie -->
<!--     <div class="card mb-3" v-for="movie in movies" v-on:click="selectedMovie = movie"  style="max-width: 540px;">
      <div class="row no-gutters">
        <div class="col-md-4">
          <router-link :to="`/movies/${movie.id}`">
          <img v-bind:src="movie.image_url" class="card-img" alt="...">
          </router-link>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <p class="card-text">{{ movie.year}}</p>
            <p class="card-text">Director: {{ movie.director}}</p> -->
           <!--  <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p> -->
  <!--         </div>
        </div>
      </div>
    </div> -->

<!--     <div v-for="movie in movies" v-on:click="selectedMovie = movie" v-bind:class="{selected: movie === selectedMovie}">
      <h2>{{ movie.title }}</h2>
      <router-link :to="`/movies/${movie.id}`">
        <img v-bind:src="movie.image_url" alt=""><br><br>
      </router-link>
    </div> -->

    <!-- Start Categories  -->
    <div class="categories-shop">
        <div class="container">
            <div v-for="movie in movies" class="row">
                <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12">
                    <div class="shop-cat-box">
                        <img class="img-fluid" v-bind:src="movie.image_url" alt="" />
                        <router-link class="btn hvr-hover" :to="`/movies/${movie.id}`">{{ movie.title }}</router-link>
                        <!-- <h2>{{ movie.title }}</h2> -->
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- End Categories -->

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
      });
  },


  methods: {}
};
</script>
