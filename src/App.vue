<script setup lang="ts">

    import { ref } from 'vue'

    import MovieCard from './components/MovieCard.vue'

    interface IMovie{

        Year: number,
        Poster: string,
        Title: string,
        Type: string

    }

    const Search = ref('')

    const SearchedMovies = ref({})

    const API_URL = 'http://www.omdbapi.com/?apikey=588d7da2';

    const SetSearch = (e: any) => {

        Search.value = e.target.value

    }

    const SearchMovies = async() => {

        const checkSearch = () => {

            return (Search.value !== '') ? `&s=${Search.value}` : ''

        }

        const response = await fetch(API_URL + checkSearch())

        const data = await response.json();

        SearchedMovies.value = data.Search;

    }

</script>

<template>

    <h1>Inside Edge</h1>

    <div class="search">

        <input        
            @change="SetSearch"
            :value="Search"
            placeholder="Search a movie..."

        />

        <img 
            src="./assets/search.svg"
            @click="SearchMovies"
        />

    </div>

    <div         
        class="container"
    >

        <div v-for="(movie, index) in SearchedMovies">
            <MovieCard :movie="movie" :key="index"/>
        </div>
<!-- 
        <div
            class="movie"
            :key="index"
            v-for="(movie, index) in SearchedMovies"
        >
            <div>
                <p>{{ movie.Year }}</p>
            </div>
            <div>
                <img 
                    :src="movie.Poster !== 'N/A' ? movie.Poster : 'https://via.placeholder.com/400'"
                />
            </div>
            <div>
                <span>{{ movie.Type }}</span>
                <h3>{{ movie.Title }}</h3>
            </div>
        </div> -->

    </div>

</template>

<style scoped>



</style>