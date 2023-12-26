<script>
import AppInfo from "@/components/AppInfo.vue";
import SearchPanel from "@/components/search-panel/SearchPanel.vue";
import AppFilter from "@/components/app-filter/AppFilter.vue";
import MovieList from "@/components/movie-list/MovieList.vue";
import MovieAddForum from "@/components/movie-add-forum/MovieAddForum.vue";

export default {
  data() {
    return {
        movies: [
          {name: 'Omar', viewers: 222},
          {name: 'Abdulhamid', viewers: 111},
          {name: 'Homid', viewers: 333},
          {name: 'Roziya', viewers: 333},
          {name: 'Tomi Stark', viewers: 333}
        ]
    }
  },
  components: {
    MovieAddForum,
    MovieList,
    AppFilter,
    SearchPanel,
    AppInfo
  },
}
</script>

<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :allMoviesCount="movies.length"/>
      <div class="search-panel">
        <SearchPanel/>
        <AppFilter/>
        <MovieList/>
      </div>
      <MovieList :movies="movies"/>
      <MovieAddForum/>
    </div>
  </div>
</template>

<style>
.search-panel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 15);

}

.app {
  height: 100vh;
  color: #000
}

.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
</style>