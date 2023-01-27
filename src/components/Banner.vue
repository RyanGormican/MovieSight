<script setup>
import getImage from "../lib/getImage"
const { } = defineProps({"banner"})
const {
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
<div class= "text-white p-10 flex flex-col justify-center w-full h-full bg-gradient-to-r from-black to-ransparent""
<h1 class ="text-8xl font-bold"> {{title}} </h1>
<p class ="mt-2 w-1/2 text-sm text-neutral-400"> {{ description }}</p>

</div>
</div>
</template>