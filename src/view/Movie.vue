<script setup>
import { useRouter } from "vue-router"
import { onMounted, ref } from "vue";
const router = useRouter()
const movieId = router.currentRoute.value.params.id
const movie=ref(null)
onMounted(async() => {
movie.value = await fetch(`https://api.themoviedb.org/3/movie/${movieId}?api_key=c46280d39e34b3012975df9f8e6e9e70`).then(res => res.json())

})
</script> 
<template>
Movie
</template>