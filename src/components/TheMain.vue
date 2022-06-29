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


export default {
  components: { MovieCard },

  data() {
      return {};
  },

  props: {
      searchText: String,
      moviesList: Array
  },

  methods: {},
}

</script>

<style>

</style>