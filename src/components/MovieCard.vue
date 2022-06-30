<template>
  <div>
    <div class="card">
        <h3>{{ movieTitle }}</h3>
        <h4>{{ originalTitle }}</h4>
        <img :src="cardImg" alt=""><br>
        <span  class="fi " :class="'fi-' + langFlag()"></span><br>
        <span v-for="i in 5" :key="i">
            <span v-if="i <= ratingVotes">
                <i class="fa-solid fa-star"></i>
            </span>
            <span v-else>
                <i class="fa-regular fa-star"></i>
            </span>
        </span>
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
    },

    cardImg() {
        const imgUrl = "https://image.tmdb.org/t/p/";
        const imgSize = "w342"

        if(this.movie.poster_path) {
            return imgUrl + imgSize + this.movie.poster_path
        }
        return "/movie-placeholder.jpg"
    },

    ratingVotes() {
        return Math.ceil(this.movie.vote_average / 2)
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
    },
}
}
</script>

<style>
</style>