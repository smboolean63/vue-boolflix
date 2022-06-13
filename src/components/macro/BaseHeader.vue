<template>
  <header>
      <form @submit.prevent="searching">
          <input type="text" v-model="searchText" required>
          <button type="submit">Search</button>
      </form>
  </header>
</template>

<script>
import axios from 'axios';
import data from '../../shared/data';

export default {
    name: 'BaseHeader',
    data() {
        return {
            data,
            searchText: '',
        }
    },
    methods: {
        searching() {
            // Films
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: this.searchText,
                    language: 'it-IT'
                }
            }).then((response) => {
                data.movies = response.data.results;
                this.searchText = '';
            }).catch((error) => {
                console.log(error);
            })

            // Serie TV
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: this.searchText,
                    language: 'it-IT'
                }
            }).then((response) => {
                data.tv = response.data.results;
                this.searchText = '';
            }).catch((error) => {
                console.log(error);
            })
        }
    }
}
</script>