<template>
  <div>
    <ul>
      <li v-for="movie in moviesList" :key="movie.id">
        <MovieCard :movie="movie"></MovieCard>
      </li>
    </ul>
  </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";
import axios from "axios"


export default {
  components: { MovieCard },

  data() {
      return {
        moviesList: []
      };
  },

  props: {
      searchText: String,
  },

  methods: {

    fetchData(type) {
      axios
      .get("https://api.themoviedb.org/3/search/" + type, {
        params: {
          api_key: "c4e62aebf2d0c0911a002c3139a7f4f9",
          query: this.searchText,
          language: "it-IT",
        }
      })
      .then((resp) => {
        this.moviesList = resp.data.results;
      })
    }
  },

  watch: {
    searchText: function() {
      this.fetchData("movie");
      this.fetchData("tv");
    }
  }
};

</script>

<style>

</style>