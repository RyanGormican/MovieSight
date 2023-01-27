<script setup>
import getImage from "../lib/getImage"
import { RouterLink } from 'vue-router';
import { Icon } from '@iconify/vue';
const { banner  } = defineProps({"banner"})
const {
id,
title,
overview: description,
backdrop_path: background,
release_date,
vote_average: vote,
original_language: language
} = banner

const image = getImage(background)
</script>

<template>
<div
class="w-screen h-screen"
:style="{
	backgroundImage: 'url'(' + getImage(background)+ ')',
	backgroundPosition: 'center center'
}">
<div class= "text-white p-10 flex flex-col justify-center w-full h-full bg-gradient-to-r from-black to-ransparent">
<h1 class ="text-8xl font-bold"> {{title}} </h1>
<p class ="mt-2 w-1/2 text-sm text-neutral-400"> {{ description }}</p>
<RouterLink :to="`/movies/${id}`"" class = "flex items-center gap-1 px-6 py-4 rounded-md bg-green-700 w-fit mt-4 transition hover:bg-neutral-800 font-semibold">
<span>View More</span>
<span> <Icon icon="ic:round-play-arrow" />
</span>
</button>
</div>
</div>
</template>