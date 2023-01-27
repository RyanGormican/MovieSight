<script setup>
import { useRouter } from "vue-router"
const router = useRouter()
const movieId = router.currentRoute.value.params.id
</script> 
<template>
Movie
</template>