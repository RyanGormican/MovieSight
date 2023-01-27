<script setup>
  import { ref, onMounted, defineAsyncComponent } from "vue"
  import Navbar from "./components/Navbar.vue";
  import MovieList from "./components/MovieList.vue";
  const movies = ref([])
  const bannerMovie = ref(null)

  const AsyncBanner = defineAsyncComponent(() => {
  return "./components/Banner.vue"
  })
  const findMovies = async () => {
  movies.value = await fetch("https://api.themoviedb.org/3/movie/popular?api_key=c46280d39e34b3012975df9f8e6e9e70")
  .then(res => res.json())
  .then(res => res.results)
  }

  const findRandom = (min, max) => {
  return Math.floor(Math.random() * (max - min) + min)
  }

  onMounted(async() => {
  await findMovies()
  bannerMovie.value = movies.value[findRandom(0, movies.value.length - 1)]
  })

</script>
<template>
  <Navbar />
  <AsyncBanner
    :banner ="bannerMovie"
/>
  <MovieList
    :movies="movies"
/>
</template>

