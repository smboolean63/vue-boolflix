<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for="film in films" :key="film.id">{{film.title}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      films: []
    }
  },
  created() {
    axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: 'e99307154c6dfb0b4750f6603256716d',
        query: 'ritorno',
        language: 'it-IT'
      }
    }).then((response) => {
      this.films = response.data.results;
    }).catch((error) => {
      console.log(error);
    })
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
