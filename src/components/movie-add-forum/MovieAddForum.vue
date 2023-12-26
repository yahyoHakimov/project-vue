<script>
export default {
  data() {
    return {
      name: '',
      viewers: ''
    }
  },
  methods: {
    addMovie() {
      const newMovie = {
        name: this.name,
        viewers: this.viewers,
        favorite: false
      }
      console.log(newMovie)
    }
  }
}
</script>

<template>
  <div class="movie-add-form">
    <h3>Yangi kino qo'shish</h3>
    <form class="add-form d-flex">
      <input type="text"
             class="form-control new-movie-label"
             placeholder="Qanday kino?"
             :value='name'
      v-on:input="name = $event.target.value ">
      <input type="number"
             class="form-control new-movie-label"
             placeholder="Necha marotaba ko'rilgan?"
             :value='viewers'
             v-on:input="name = $event.target.value"
      >

      <button class="btn btn-outline-dark" type="submit">
        Qo'shish
      </button>
    </form>
  </div>
</template>

<style>
.movie-add-form {

  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 15);
}
</style>