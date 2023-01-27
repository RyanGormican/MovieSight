<script setup>
import getImage from '../lib/getImage';
import { Icon } from '@iconify/vue';
const { movie } = defineProps(["movie"])
const {
	title,
	overview,
	backdrop_path: background,
	poster_path: poster,
	release_date,
	vote_average: vote,
	original language: language
} = movie
</script>

<template>
<div>
a
</div>
</template>