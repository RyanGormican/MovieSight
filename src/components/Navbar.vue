<script setup>
import { Icon } from '@Iconify/vue';
</script> 
<template>
<nav class="flex text-white items-center gap-20 absolute left-0 right-0 mx-6 py-4 top-4 bg-transparent border-b-2 border-neutral-400">
	<div class="flex text-3xl items-center font-bold gap-2">
	<Icon icon= "mingcute:movie-line" width = "40" />
	<span> MovieSight</span>
	</div>
	<ul class="flex items-center gap-4 font-semibold">
	 <li>Movies</li>
	 <li>Favourite Movies</li>
	</ul>
</nav>
</template>