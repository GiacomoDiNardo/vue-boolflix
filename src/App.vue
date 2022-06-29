<template>
  <div id="app">
    <SearchBar @searchingText="onSearchingText"></SearchBar>
    <TheMain :searchText="searchText" :moviesList="moviesList"></TheMain>
  </div>
</template>

<script>
import axios from "axios"
import SearchBar from './components/SearchBar.vue';
import TheMain from './components/TheMain.vue';


export default {
  name: 'App',
  components: {
    SearchBar,
    TheMain
},

data() {
  return {
    searchText: "",
    moviesList: []
  }
},

methods: {
  onSearchingText(searchText) {
    this.searchText = searchText;

    axios
    .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "c4e62aebf2d0c0911a002c3139a7f4f9",
          query: this.searchText,
          language: "it-IT",
        }
      })
      .then((resp) => {
        this.moviesList = resp.data.results;
      })
  },
}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
