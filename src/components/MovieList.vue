<script setup>
import MovieCard from './MovieCard.vue';
const { movies } = defineProps({
movies: Array
})
</script>
<template>
<div class ="grid grid-cols-3 gap-4 mx-20 my-10">
	<MovieCard
	 v-for="movie in movies"
	:movie="movie"
	/>
</div>
</template>