<template>
    <main>
        <ul>
            <li v-for="movie in data.movies" :key="movie.id">
                <h3>{{movie.title}}</h3>
                <h4>{{movie.original_title}}</h4>
                <p>{{movie.vote_average}}</p>
                <p><img :src="existFlag(movie.original_language) ? require(`../../assets/flags/${movie.original_language}.png`) : null"></p>
            </li>
        </ul>
    </main>
</template>

<script>
import data from '../../shared/data';

export default {
    name: 'BaseMain',
    data() {
        return {
            data,
            flagsAviable: [
                'en'
            ]
        }
    },
    methods: {
        existFlag(lang) {
            return this.flagsAviable.includes(lang);
        }
    }
}
</script>