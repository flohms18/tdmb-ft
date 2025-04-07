<template>
  <div>
    <h1>Popular Movies</h1>
    <input placeholder="Enter the name of our favorite movie!" v-model="UserMovie">
    <button @click="fetchPopularMovies">Fetch Popular Movies</button>
    <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
    <div>
      <label for="movies" v-if="movies.length">Choose a Movie:</label>
      <select id="movies" name="movies">
        <option value="{{ movie.title }}" v-for="movie in movies" key="movie.id">{{ movie.title }}</option>
      </select> 
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      movies: [],          // Array to store movie data
      loading: false,      // Loading state
      errorMessage: '',    // Error message
      apiKey: '27beba95fd51654379e58b8e53c1c594',  // Replace with your TMDb API key
      apiUrl: 'https://api.themoviedb.org/3', // Base API URL
      UserMovie : '',
      SavedMovie : '',
      TsavedMovie : ''
    };
  },
  methods: {
    TransformSearchMovie() {
      this.SavedMovie = this.UserMovie
      this.TsavedMovie = this.SavedMovie.split(' ').join('%20')
      console.log(this.TsavedMovie)
     
    },

    async fetchPopularMovies() {
      this.TransformSearchMovie()
      this.loading = true;
      this.errorMessage = '';
      try {
        const response = await axios.get(
          `${this.apiUrl}/search/movie?query=${this.TsavedMovie}`, {
            params: {
              api_key: this.apiKey,
              language: 'en-US',         
            }
          }
        );
        this.movies = response.data.results;
        this.loading = false;
      } catch (error) {
        this.errorMessage = 'Failed to fetch movies: ' + error.message;
        this.loading = false;
      }
    }
  }
}
</script>

<style scoped>
.error {
  color: red;
}
</style>
