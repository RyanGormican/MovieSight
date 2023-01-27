<script setup>
import getImage from '../lib/getImage';
import { Icon } from '@iconify/vue';
const { movie } = defineProps(["movie"])
const {
	title,
	overview: description,
	backdrop_path: background,
	poster_path: poster,
	release_date,
	vote_average: vote,
	original language: language
} = movie
</script>

<template>
<div class="w-full h-full grid grid-rows-[4fr_1fr]">
	<div class="relative group w-full h-full">
	<img
	:src="getImage(poster)"
	/>
	<div 

	</div>
	</div>
</div>
</template>