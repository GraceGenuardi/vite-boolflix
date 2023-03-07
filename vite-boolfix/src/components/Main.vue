<template>
    <main class="main">
      <!-- SEARCHBAR -->
      <div class="col-2 search">
        <form @submit.prevent="searchMedia">
          <input type="text" v-model="searchTerm" placeholder="Cerca un film o una serie tv" />
          <button type="submit"><i class="fa-solid fa-magnifying-glass"></i></button>
        </form>
      </div>
      <h2 class="text-light">Risultati della tua ricerca:</h2>
  <div v-if="mediaResults.length" class="text-light d-flex m-5">
    <div v-for="media in mediaResults" :key="media.id" class="mx-3">
      <h2>{{ media.title || media.name }}</h2>
      <p>{{ media.original_title || media.original_name }}</p>
      <p v-if="media.original_language">
        <i v-if="getFlag(media.original_language)" :class="getFlag(media.original_language)"></i>
        {{ media.original_language }}
      </p>
      <p>{{ media.vote_average }}</p>
    </div>
  </div>
    </main>
  </template>
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        searchTerm: "",
        mediaResults: [],
      };
    },
  
    methods: {
      searchMedia() {
        axios
          .all([
            axios.get("https://api.themoviedb.org/3/search/movie", {
              params: {
                api_key: "c706f94ce5d14347af05f5cc11f3de87",
                query: this.searchTerm,
                language: "it-IT",
              },
            }),
            axios.get("https://api.themoviedb.org/3/search/tv", {
              params: {
                api_key: "c706f94ce5d14347af05f5cc11f3de87",
                query: this.searchTerm,
                language: "it-IT",
              },
            }),
          ])
          .then(
            axios.spread((moviesRes, tvShowsRes) => {
              const movies = moviesRes.data.results.map((movie) => ({
                ...movie,
                media_type: "movie",
              }));
              const tvShows = tvShowsRes.data.results.map((tvShow) => ({
                ...tvShow,
                media_type: "tv",
              }));
              this.mediaResults = [...movies, ...tvShows];
            })
          )
          .catch((error) => {
            console.log(error);
          });
      },
  
      getFlag(language) {
        switch (language) {
          case "it":
            return "flag-icon flag-icon-it";
          case "en":
            return "flag-icon flag-icon-gb";
          case "fr":
            return "flag-icon flag-icon-fr";
          
          default:
            return "";
        }
      },
    },
  };
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