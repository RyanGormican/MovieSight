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
</script>

<template>

<h1>{{title }}</h1>
</template>