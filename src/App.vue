<script setup>
  import { ref, onMounted } from "vue"
  const movies = ref()
  const getMovies = async () => {
  await fetch("https://api.themoviedb.org/3/movie/550?api_key=c46280d39e34b3012975df9f8e6e9e70")
  }
</script>
<template>
  <h1> Hello World</h1>
</template>

