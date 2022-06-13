<template>
    <main>
        <section>
            <h2>Films</h2>
            <ul>
                <li v-for="movie in data.movies" :key="movie.id">
                    <BaseCard :info="movie"/>
                </li>
            </ul>
        </section>
        <section>
            <h2>Serie TV</h2>
            <ul>
                <li v-for="tv in data.tv" :key="tv.id">
                    <BaseCard :info="tv"/>
                </li>
            </ul>
        </section>
    </main>
</template>

<script>
import data from '../../shared/data';
import BaseCard from '../commons/BaseCard.vue';

export default {
    name: 'BaseMain',
    components: {
        BaseCard
    },
    data() {
        return {
            data,
        }
    },
}
</script>