<template>
  <div class="home container">
    <h1>{{ message }}</h1>
    <div v-for="beer in products">
      <h2>{{ beer.name }}</h2>
      <h4>{{ beer.description }}</h4>
      <h4>${{ beer.price }}0</h4>
      <p>{{ beer.supplier.name }}</p>
      <img v-bind:src="beer.images[0]" alt="No Image" width="350">
    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      message: "Microbrewery Menu",
      products: []
    };
  },
  created: function() {
    axios.get("http://localhost:3000/api/beers").then(
      function(response) {
        console.log(response);
        this.products = response.data.beers;
      }.bind(this)
    );
  },
  methods: {},
  computed: {}
};
</script>
