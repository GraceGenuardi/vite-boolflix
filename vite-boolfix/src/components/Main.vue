<template>
    <main class="main">
  <!-- SEARCHBAR -->
   <div class="col-2 search"> 
    
    
    <form @submit.prevent="searchMovies">
             <input type="text" v-model="searchTerm" placeholder="Cerca un film">
             <button type="submit"><i class="fa-solid fa-magnifying-glass"></i></button>
          </form>

          <div v-if="movies.length">
              <div v-for="movie in movies" :key="movie.id">
                 <h2>{{ movie.title }}</h2>
                 <p>{{ movie.original_title }}</p>
                 <p>{{ movie.original_language }}</p>
                 <p>{{ movie.vote_average }}</p>
              </div>
         </div>

           
     
  
  
    </div>   
    </main>
  
  </template>
  
  <script>
  
  import axios from 'axios';

  export default {
    data() {
      return {
        searchTerm: '',
        movies: []
      }
    },

    methods: {
      searchMovies() {
        axios.get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: 'c706f94ce5d14347af05f5cc11f3de87',
            query: this.searchTerm
          }
        })
        .then(response => {
          this.movies = response.data.results;
        })
        .catch(error => {
          console.log(error);
        });
      }
    }
  }
  
  </script>
  
  <style lang="scss" scoped>
  .main {
    padding: 50px 0;
    background-color: rgb(15, 11, 11);
  }
  .container-main{
    width: 1200px;
    margin-left: 350px;
  }

  .search {
    position: relative;
   
    left: 1600px;
    bottom: 100px;
    
  }
  
  </style>