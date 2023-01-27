<script setup>
const { } = defineProps({"banner"})
const {
title,
overview: description,
bacdrop_path: background,
release_date,
vote_average: vote,
original_language: language
} = banner
const image = 'https;//image.tmdb.org/t/p/original/$(backround)'
</script>

<template>
<div>
<img
:src="image"
/>
<h1>{{title }}</h1>
</div>
</template>