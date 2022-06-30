<template>
  <div>
    <div class="card">
        <h3>{{ movieTitle }}</h3>
        <h4>{{ originalTitle }}</h4>
        <span  class="fi " :class="'fi-' + langFlag()"></span><br>
        <span>{{ movie.vote_average }}</span>
    </div>
  </div>
</template>

<script>
export default {
props: {
    movie: Object
},

  computed: {
    movieTitle() {
        if(this.movie.title) {
            return this.movie.title;
        }
        return this.movie.name;
    },

    originalTitle() {
        if(this.movie.original_title) {
            return this.movie.original_title;
        }
        return this.movie.original_name
    }
  },

methods: {
    langFlag() {
        const langsMap = {
            "en" : "us",
            "ja" : "jp",
            "ko" : "kr"
        };
        if (langsMap[this.movie.original_language]) {
            return langsMap[this.movie.original_language]
        }

        return this.movie.original_language;
    }
}
}
</script>

<style>
</style>