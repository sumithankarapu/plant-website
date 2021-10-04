<template>
  <div id="nav">
    <router-link to="/">Home</router-link> 
    <h1 class id ="main-heading">P l a n t a e</h1>
    <router-link v-bind:to="{ name: 'About' }">About</router-link>
  </div>
  <router-view/>
</template>

<style>
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  font-family:"Roboto";
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #023315;
  color: rgb(38, 130, 236);
  padding: 20px 50px;
  margin-bottom:0;
}

#nav a {
  font-size: 25px;
  color:  hsl(32, 48%, 82%);
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: hsl(266, 52%, 82%);
  text-decoration:underline;
  
}
#main-heading{
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  font-style: italic;
  font-weight: bolder;
  color:rgb(224, 178, 189)
  
}
</style>
