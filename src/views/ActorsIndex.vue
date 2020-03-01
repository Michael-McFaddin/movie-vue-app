<template>
  <div class="actors-index">

    <div v-for=" actor in actors">
      <h3>{{ actor.first_name + " " + actor.last_name }}</h3>
      <h4>Age: {{ actor.age }}</h4>
      <h4>Known for: {{ actor.known_for }}</h4><br><br>
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
      actors: []
    };
  },

  created: function() {
    axios
      .get("/api/actors")
      .then(response => {
        this.actors = response.data;
      });
  },


  methods: {}
};
</script>