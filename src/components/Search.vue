<template>
  <div class='search'>
    <h1>Searchh</h1>
    <input type='text' v-model='query' @keyup='getResult'>
    <div v-for='result in results' :key='result.id'>
      <p>{{ result.title }}</p>
      <img v-bind:src="'http://image.tmdb.org/t/p/w500/' + result.poster_path" width='100px'>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'search',
  data () {
    return {
      query: '',
      results: []
    }
  },
  methods: {
    getResult() {
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=2842841078a4f6bfc31aefd8209023d7&query=' + this.query)
        .then(response => {
          this.results = response.data.results 
        })
      console.log(this.results)
    }
  }
}
</script>