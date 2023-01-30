<script setup>
	import { useRouter } from "vue-router"
	import { ref } from "vue";
	import { Icon } from "@iconify/vue"
	import getImage from "../lib/getImage"
	const router = useRouter()
	const movieId = router.currentRoute.value.params.id
	const movie = ref(null)
	movie.value = await fetch(`https://api.themoviedb.org/3/movie/${movieId}?api_key=c46280d39e34b3012975df9f8e6e9e70`).then(res => res.json())
	const {
		title,
		overview: description,
		backdrop_path: background,
		poster_path: poster,
		release_date,
		vote_average: vote,
		popularity,
		runtime,
		original_language: language,
		budget,
		revenue,
		tagline,
		production_companies,
		production_countries,
		genres
	} = movie.value
</script>
<template>
	<div class="h-screen w-screen grayscale-0" :style="{
backgroundImage: 'url(' +getImage(background)+')'
	}">
		<div class="w-full h-full bg-gradient-to-r from-black to-transparent">
			<div class="pt-20 w-full h-full grid grid-cols-2 items-center">
				<img class="w-[400px] mx-auto rounded-lg" :src="getImage(poster)" />
				<div>
					<h1 class="text-4xl font-semibold mb-4">{{ title }}</h1>
					<p class="text-sm text-neutral-300 w-2/3">{{ description }}</p>
					<div class="flex flex-col text-sm gap-2 mt-3">
						<div class="flex items-center gap-2" v-if="tagline.length>0">
							<Icon icon="emojione-monotone:left-speech-bubble" />
							<span>{{ tagline }} </span>
						</div>
						<div class="flex items-center gap-2 ">
							<div class="flex items-center gap-2" v-for="genre in genres">
								<Icon icon="ph:sword" v-if="genre.name === 'Action'" />
								<Icon icon="material-symbols:map" v-if="genre.name === 'Adventure'" />
								<Icon icon="mdi:film-reel" v-if="genre.name === 'Animation'" />
								<Icon icon="ri:emotion-laugh-fill" v-if="genre.name === 'Comedy'" />
								<Icon icon="mdi:gun" v-if="genre.name === 'Crime'" />
								<Icon icon="game-icons:drama-masks" v-if="genre.name === 'Drama'" />
								<Icon icon="icon-park-outline:family" v-if="genre.name === 'Family'" />
								<Icon icon="fa6-solid:wand-sparkles" v-if="genre.name === 'Fantasy'" />
								<Icon icon="mdi:scroll-text-outline" v-if="genre.name === 'History'" />
								<Icon icon="material-symbols:skull" v-if="genre.name === 'Horror'" />
								<Icon icon="ion:musical-notes-sharp" v-if="genre.name === 'Music'" />
								<Icon icon="ph:detective" v-if="genre.name === 'Mystery'" />
								<Icon icon="mdi:alien" v-if="genre.name === 'Science Fiction'" />
								<Icon icon="ri:knife-blood-line" v-if="genre.name === 'Thriller'" />
								<Icon icon="healthicons:war" v-if="genre.name === 'War'" />
								<span>{{ genre.name }} </span>
							</div>
						</div>
						<div class="flex items-center gap-2">
							<Icon icon="uiw:date" />
							<span>{{ release_date }} </span>
						</div>
						<div class="flex items-center gap-2">
							<Icon icon="ic:round-star" />
							<span>{{ vote }} / 10 </span>
						</div>
						<div class="flex items-center gap-2">
							<Icon icon="ion:people" />
							<span>{{ popularity }} </span>
						</div>
						<div class="flex items-center gap-2" v-if="budget!== 0 && revenue !== 0">
							<Icon icon="uil:money-bill" />
							<span> $ {{ revenue.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,') }} </span>
							<Icon icon="uil:money-bill-slash" />
							<span> $ {{ budget.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,') }} </span>
						</div>
						<div class="flex items-center gap-2">
							<Icon icon="ic:twotone-access-time-filled" color="white" />
							<span>{{ runtime }} minutes</span>
						</div>
						<div class="flex items-center gap-3 ">
							<div class="flex items-center gap-2" v-for="company in production_companies">
								<img class="w-8" :src="getImage(company.logo_path)" crossorigin="anonymous" v-if="getImage(company.logo_path)!='https://image.tmdb.org/t/p/original/null'"/>
								<span>{{ company.name }} </span>
							</div>
						</div>
						<div class="flex items-center gap-2 ">
							<div class="flex items-center gap-2" v-for="country in production_countries">
								<img class="w-8" :src="`https://countryflagsapi.com/png/${country.iso_3166_1.toLowerCase()}`" crossorigin="anonymous" />
								<span>{{country.name }} </span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>