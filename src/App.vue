<template>
  <div id="app">
    <SearchBar @searchingText="onSearchingText"></SearchBar>
    <TheMain :searchText="searchText"></TheMain>
  </div>
</template>

<script>
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
  }
},

methods: {
  onSearchingText(searchText) {
    this.searchText = searchText;
  },

  
}
}
</script>

<style lang="scss">
@import "./assets/scss/main";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
