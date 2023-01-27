<script setup>
const { movies } = defineProps({
movies: Array
})
</script>
<template>
<div class ="grid grid-cols-3 gap-4 mx-20 my-10">
	<div v-for="movie in movies">
		{{ movie.title }}
	</div>
</div>
</template>