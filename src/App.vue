<template>
  <div id="app">

    <!-- bootstrap nav bar -->
  <!--   <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="/">Mike's Movies</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active"> -->
            <!-- below, original code before adding router-link -->
            <!-- <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a> -->
  <!--           <router-link v-if="isLoggedIn()" class="nav-link" to="/movies">All Movies<span class="sr-only">(current)</span></router-link>
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
    </nav> -->

        <!-- Start Main Top  theme nav bar -->
    <header class="main-header">
        <!-- Start Navigation -->
        <nav class="navbar navbar-expand-lg navbar-light bg-light navbar-default bootsnav">
            <div class="container">
                <!-- Start Header Navigation -->
                <div class="navbar-header">
                    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbar-menu" aria-controls="navbars-rs-food" aria-expanded="false" aria-label="Toggle navigation">
                    <i class="fa fa-bars"></i>
                </button>
                   <h1>Mike's Movies</h1>
                </div>
                <!-- End Header Navigation -->

                <!-- Collect the nav links, forms, and other content for toggling -->
                <div class="collapse navbar-collapse" id="navbar-menu">
                    <ul class="nav navbar-nav ml-auto" data-in="fadeInDown" data-out="fadeOutUp">
                        <li class="nav-item"><router-link v-if="isLoggedIn()" class="nav-link" to="/movies">All Movies</router-link></li>
                        <li class="nav-item"><router-link v-if="isLoggedIn()" class="nav-link" to="/movies/new">Add Movies</router-link></li>
                        <li class="nav-item"><router-link v-if="isLoggedIn()" class="nav-link" to="/actors">Actors</router-link></li>
                        <li class="nav-item"><router-link v-if="!isLoggedIn()" class="nav-link" to="/signup">Sign Up</router-link></li>
                        <li class="nav-item"><router-link v-if="!isLoggedIn()" class="nav-link" to="/login">Log In</router-link></li>
                        <li class="nav-item"><router-link v-if="isLoggedIn()" class="nav-link" to="/logout">Log out</router-link></li>
                    </ul>
                </div>
                <!-- /.navbar-collapse -->

            </div>
        </nav>
        <!-- End Navigation -->
    </header>
    <!-- End Main Top theme nav bar -->


    
    <!-- original nav bar -->
   <!--  <div id="nav">
      These router links get converted to <a> tags when sent to the browser 
      <router-link to="/">Home</router-link> |
      <router-link v-if="isLoggedIn()" to="/movies">All Movies</router-link> |
      <router-link v-if="isLoggedIn()" to="/movies/new">Add Movies</router-link> |
      <router-link v-if="!isLoggedIn()" to="/signup">Signup</router-link> |
      <router-link v-if="!isLoggedIn()" to="/login">Login</router-link> |
      <router-link v-if="isLoggedIn()" to="/logout">Logout</router-link> |
    </div> -->

    <div class="container">
      <!-- every individual view file gets interpolated here  -->
      <router-view/>
    </div>

    <!-- Start Footer  -->
    <footer>
        <div class="footer-main">
            <div class="container">
          <div class="row">
            
            <div class="col-lg-4 col-md-12 col-sm-12">
              <div class="footer-top-box">
                <h3>Social Media</h3>
                <ul>
                  <li><a href="#"><i class="fab fa-facebook" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fab fa-twitter" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fab fa-linkedin" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fab fa-google-plus" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fa fa-rss" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fab fa-pinterest-p" aria-hidden="true"></i></a></li>
                  <li><a href="#"><i class="fab fa-whatsapp" aria-hidden="true"></i></a></li>
                </ul>
              </div>
            </div>
          </div>
            <hr>
                <div class="row">
                    <div class="col-lg-4 col-md-12 col-sm-12">
                        <div class="footer-widget">
                            <h4>About Mike's Movies</h4>
                            <p>These are some movies I like. Please check them out when you have time.</p>                
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </footer>
    <!-- End Footer  -->
 
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

