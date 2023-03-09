<template>
  <main class="main">
    <!-- SEARCHBAR -->
    <div class="col-2 search">
      <div v-if="!isInputOpen">
        <button @click="toggleInput" class="text-danger bg-dark"><i class="fa-solid fa-magnifying-glass"></i> Cerca film e serie</button>
      </div>
      <div v-else>
        <form @submit.prevent="searchMedia">
          <input type="text" v-model="searchTerm" placeholder="Cerca un film o una serie tv" class="text-danger"/>
        </form>
      </div>
    </div>

    <h2 class="text-light">Risultati della tua ricerca:</h2>

    <div v-if="mediaResults.length" class="row p-3 px-5 mx-5 text-light ">
      <div v-for="(media, index) in mediaResults" :key="media.id" class="col-2 border border-danger mb-4 mx-5 px-5">
        <h3 class="fs-5 m-3">{{ media.title || media.name }}</h3>
        <img :src="media.poster_path" alt="Poster"/>
        <p class=" p-3 text-center">{{ media.original_title || media.original_name }}</p>
        <p v-if="media.original_language" class=" pb-3 text-center position-static">
          <i v-if="getFlag(media.original_language)" :class="getFlag(media.original_language)"></i>
          {{ media.original_language }}
        </p>
        
        <div class="stars">
            <i v-for="n in Math.ceil(media.vote_average / 2)" class="fa-solid fa-star"></i>
            <i v-for="n in Math.floor((10 - media.vote_average) / 2)" class="far fa-star"></i>
        </div>  
        
      </div>
      <div v-if="(index + 1) % 4 === 0" class="w-100"></div>
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
      isInputOpen: false,
      currentMedia: null
    };
  },

  methods: {
    toggleInput() {
      this.isInputOpen = !this.isInputOpen;
    },

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
             //MILSTONE 3
              poster_path: "https://image.tmdb.org/t/p/w342" + movie.poster_path,
            }));
            const tvShows = tvShowsRes.data.results.map((tvShow) => ({
              ...tvShow,
              media_type: "tv",
              poster_path: "https://image.tmdb.org/t/p/w342" + tvShow.poster_path,
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
    padding: 10px 10px;
    background-color: black;
  }
  .container-main{
    width: 1200px;
    margin-left: 350px;
    padding: 10px;
  }

  .search {
    position: relative;
    left: 1600px;
    bottom: 55px;
  }

  /**POSTER RULES **/
  .col-2 {
  position: relative;
  
  
}

img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 0 auto;
}

.stars {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  color: rgb(255, 208, 0);
}

  
  
  </style>