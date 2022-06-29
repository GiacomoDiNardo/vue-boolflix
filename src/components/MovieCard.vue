<template>
  <div>
    <div class="card">
        <h3>{{ movie.title }}</h3>
        <h4>{{ movie.original_title }}</h4>
        <span>{{ movie.original_language }}</span><br>
        <span>{{ movie.vote_average }}</span>
    </div>
  </div>
</template>

<script>
export default {
props: {
    movie: Object
}
}
</script>

<style>

</style>