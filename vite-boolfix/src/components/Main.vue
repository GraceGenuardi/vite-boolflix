<template>
    <main class="main">
  
     
  
  
      
    </main>
  
  </template>
  
  <script>
  import axios from 'axios'
  
  </script>
  
  <style lang="scss" scoped>
  .main {
    padding: 50px 0;
    background-color: black;
  }
  .container-main{
    width: 1200px;
    margin-left: 350px;
  }
  .cards {
    display: grid;
    grid-template-columns: repeat(4,1fr);
    background-color: rgba(255, 255, 255, 0.586);
    padding: 50px;
  }
  .found{
    color: white;
    position: relative;
    width: 1075px;
    left: 70px;
    top: 75px;
    background-color: rgb(47, 47, 47);
    text-align: left;
    padding: 10px;
    
  }
  /**MENU RULES */
  .filter {
    background-color: rgb(255, 104, 10);
    margin-bottom: 25px;
    display: flex;
    width: 220px;
    margin-left: 360px;
    padding: 5px;
    border-radius: 5px;
  }
  .filter i{
    color: white;
    margin-top: 3px;
    margin-right: 3px;
  }
  </style>