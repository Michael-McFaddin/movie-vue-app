<template>
  <div id="app">

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="/">Mike's Movies</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <!-- below, original code before adding router-link -->
            <!-- <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a> -->
            <router-link v-if="isLoggedIn()" class="nav-link" to="/movies">All Movies<span class="sr-only">(current)</span></router-link>
          </li>
          <li class="nav-item">
            <router-link v-if="isLoggedIn()" class="nav-link" to="/actors">Actors</router-link>
          </li>
          <li class="nav-item">
            <router-link v-if="isLoggedIn()" class="nav-link" to="/movies/new">Add Movies</router-link>
          </li>
          <li class="nav-item">
            <router-link v-if="!isLoggedIn()" class="nav-link" to="/signup">Signup</router-link>
          </li>
          <li class="nav-item">
            <router-link v-if="!isLoggedIn()" class="nav-link" to="/login">Login</router-link>
          </li>
          <li class="nav-item">
            <router-link v-if="isLoggedIn()" class="nav-link" to="/logout">Logout</router-link>
          </li>
          <li class="nav-item">
            <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
          </li>
        </ul>
      </div>
    </nav>
    
    <!-- original nav bar -->
    <!-- <div id="nav"> -->
      <!-- These router links get converted to <a> tags when sent to the browser  -->
      <!-- <router-link to="/">Home</router-link> | -->
      <!-- <router-link v-if="isLoggedIn()" to="/movies">All Movies</router-link> | -->
      <!-- <router-link v-if="isLoggedIn()" to="/movies/new">Add Movies</router-link> | -->
      <!-- <router-link v-if="!isLoggedIn()" to="/signup">Signup</router-link> | -->
      <!-- <router-link v-if="!isLoggedIn()" to="/login">Login</router-link> | -->
      <!-- <router-link v-if="isLoggedIn()" to="/logout">Logout</router-link> | -->
    <!-- </div> -->

    <div class="container">
      <!-- every individual view file gets interpolated here  -->
      <router-view/>
    </div>
 
  </div>
</template>

<style>
 img {
    width: 250px;
  }
</style>

<script>
export default {
  
  methods: {
    isLoggedIn: function() {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function() {
      return localStorage.getItem("user_id");
    }
  }
};
</script>

