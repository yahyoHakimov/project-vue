<script>
export default {
  props: {
    allMoviesCount: {
      type: Number,
      required: true
    }
  }
}
</script>

<template>
  <div class="app-info">
    <p class="fs-3 text-uppercase">Barcha kinolar soni: {{allMoviesCount}}</p>
    <p class="fs-4 text-uppercase">Ko'rilgan kinolar soni: 0</p>

  </div>
</template>

<style scoped>
.app-info  {
  padding: 1.5rem;
  border-radius: 4px;
  background-color: #fcfad5;
  box-shadow: 15px 15px 15px rgba(0,0,0,0.15);
}
</style>