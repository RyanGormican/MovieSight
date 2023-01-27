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
	class="w-full h-full transition rounded-md group-hover:blur-sm cursor-pointer"
	/>
	<div class ="group-hover:opacity-100 transition-opacity opacity-0 absolute left-[-50%] top-[50%] translate-x-[50%] flex flex-col gap-2 w-full font-semibold text-white">
		<div class="w-full flex-col items-center justify-center">
		<button>
			<Icon icon="ic:around-play-arrow" width="60" class="hover:text-emerald-600"/>
		</button>
		</div>
	</div>
	<div class="absolute top-4 right-4 px-2 bg-emerald-700 py-1 rounded-md">
	<p class="flex items-center gap-1 justify-center">
		<span>{{ vote }}</span>
		<Icon icon="material-symbols:star-rounded" color="white" />
	</p>
	</div>
	<div>
	<h1 class="text-xl font-semibold my-2">{{ tile }} </h1>"
	<p class="text-neutral-400">{{ description }}</p>
	</div>
	</div>
</div>
</template>