<template>
    
    <header class="main-header">

     
        <div class="row">
            
     
         <!-- NAVBAR -->
          <nav class="navbar navbar-expand-lg navbar-light bg-light mx-5">
            <a class="navbar-brand text-danger" href="#">BOOLFLIX</a>
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
                <li class="nav-item active">
                  <a class="nav-link" href="#">Serie tv</a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" href="#">Film</a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" href="#">Nuovi e Popolari</a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" href="#">La mia lista</a>
                </li>
              </ul>
          </div>
         </nav>

        


      </div>
     
    </header>
</template>
  
  <script>
  
</script>

  
  <style lang="scss" scoped>
  @use '../style/partials/variables' as *;
  .main-header {
    text-align: left;
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