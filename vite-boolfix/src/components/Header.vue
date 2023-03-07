<template>
    
      <header class="main-header">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">BOOLFLIX</a>
          <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
  
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="#">Home</a>
              </li>
            </ul>
  
            <form class="form-inline my-2 my-lg-0" @submit.prevent="searchMovies">
              <input class="form-control mr-sm-2" type="search" placeholder="Cerca un film" aria-label="Search" v-model="searchTerm" />
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Cerca</button>
            </form>
          </div>
        </nav>
      </header>
    </template>
  
  <script>
    
  </script>
  
  <style lang="scss" scoped>
  @use '../style/partials/variables' as *;
  .main-header {
    text-align: left;
    font-size: 10px;
    background-color: white;
    padding: 5px;
    font-size: 15px;
    color: black;
    width: 1920px;
    
  }
  .logo {
    width: 100px;
    padding-right: 10px;
  }
  </style>