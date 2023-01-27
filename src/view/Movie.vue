<script setup>
import { useRouter } from "vue-router"
import { onMounted, ref } from "vue";
import getImage from '../lib/getImage"
const router = useRouter()
const movieId = router.currentRoute.value.params.id
const movie=ref(null)
onMounted(async() => {
movie.value = await fetch(`https://api.themoviedb.org/3/movie/${movieId}?api_key=c46280d39e34b3012975df9f8e6e9e70`).then(res => res.json())

})
const {
title,
overview: description,
backdrop_path: background,
release_date,
vote_average: vote,
original_language: language
} = movie.value
</script> 
<template>
<div class="h-screen w-screen grayscale-0"
:style="{
backgroundImage= 'url(' +getImage(background)+')'
}"
</div>
</template>