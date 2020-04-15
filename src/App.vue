<template>
  <div id="app">

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

                <!-- Nav links for toggling -->
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

