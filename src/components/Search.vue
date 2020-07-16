<template>
  <div class="container-fluid">
    <div class="page-header">
    	<h1>Movies</h1>
    </div>
    <div>
      <div v-for='result in results' :key='result.id' class="col-xs-6 col-sm-4 col-md-3 col-lg-2">
        <div class="thumbnail">
          <p>{{ result.title }}</p>
          <img v-bind:src="'http://image.tmdb.org/t/p/w500/' + result.poster_path" width='100px' class="poster">
        </div>
      </div>
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
      axios.get('https://api.themoviedb.org/3/movie/popular', {
        params: {
          api_key: '2842841078a4f6bfc31aefd8209023d7',
          language: 'en-US',
          page: 2,
          region:'ID'
        }
      })
        .then(response => {
          this.results = response.data.results 
        })
      console.log(this.results)
    }
  },
  mounted() {
    this.getResult()
  }
}
</script>