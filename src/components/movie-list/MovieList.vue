<script>
import MovieListItem from "@/components/movie-list-item/MovieListItem.vue";

export default {
  props: {
    movies: {
      type: Array,
      required: true
    }
  },
  components: {
    MovieListItem
  }
}
</script>

<template>
  <ul class="movie-list list-group">
    <MovieListItem v-for="movie in movies"
                   v-bind:movie="movie"
                   @onLike="$emit('onLike', movie.id)"
                   @onRemove="$emit('onRemove', $event)"

    />
  </ul>
</template>

<style>
.movie-list {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 15);

}
</style>