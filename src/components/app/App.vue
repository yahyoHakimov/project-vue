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
          {name: 'Omar', viewers: 222, id: 1},
          {name: 'Abdulhamid', viewers: 111, id: 2},
          {name: 'Homid', viewers: 333, id: 3},
          {name: 'Roziya', viewers: 333, id: 4},
          {name: 'Tomi Stark', viewers: 333, id: 5}
        ],
      term: '',
      filter: 'mostViewers'
    }
  },
  methods: {
    createMovie(item, secondItem) {
      if (item.viewers || item.name) {
        this.movies.push(item)
      } else {
        return;
      }
    },
    onLikeHandler(id) {
      const arr = this.movies.map(item => {
        if (item.id == id) {
          item.like = true
        }
        return item;
      })
      console.log(arr)
    },
    onRemoveHandler(id) {
        this.movies = this.movies.filter(c => c.id !== id)
    },
    onSearchHandler(arr, term) {
      if (term.length === 0) {
        return arr;
      }
      return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
    },
    onFilterHandler(arr, filter) {
      switch (filter) {
        case 'popular':
          return arr.filter(c => c.like)
        case 'mostViewers':
          return arr.filter(c => c.viewers > 500)
        default: return arr;
      }

    },
    updateTermHandler(term) {
      this.term = term
    },
    updateFilterHandler(filter) {
      this.filter = filter
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
        <SearchPanel :updateTermHandler="updateTermHandler"/>
        <AppFilter :update-filter-handler="updateTermHandler" :filterName="filter" />
        <MovieList :movies="onSearchHandler(movies, term)"/>
      </div>
      <MovieList :movies="onFilterHandler(onSearchHandler(movies, term), filter)"
                 :key="movies.id"
                 @onLike='onLikeHandler'
                 @onRemove='onRemoveHandler'

      />
      <MovieAddForum @createMovie="createMovie"/>
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