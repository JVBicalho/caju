<template>
  <div id="app" >
    
    <nav class="navbar navbar-expand-lg navbar-dark shadow-lg" style="background-color: #037058;">
      <a class="navbar-brand" href="#">Caju</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarTogglerDemo02"
        aria-controls="navbarTogglerDemo02"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
          <li class="nav-item ">
            <router-link class="nav-link" href="#" to="/" >
              Home
              
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" href="#" to="/about" >Sobre</router-link>
          </li>
          
        </ul>
       
      </div>
    </nav>
    
    <div class="container">
      <router-view />

    </div>

    
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
/* color palete 
#01c9a4
#109075
#a6c6bf
#037058
#897f7b */
.btn-p1{
  background-color: #109075 !important;
  color: #f2f2f2 !important;
}
.btn-p1-outline {
  color: #109075 !important;
    border-color:#109075 !important;
}
</style>
