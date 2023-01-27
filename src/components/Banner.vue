<script setup>
import getImage from "../lib/getImage"
const { } = defineProps({"banner"})
const {
title,
overview: description,
bacdrop_path: background,
release_date,
vote_average: vote,
original_language: language
} = banner
const image = getImage(background)
</script>

<template>
<div>

</div>
</template>