<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>-->
    <div class="nav">
      <div class="nav__title">
        <router-link to="/">The Stockdale Cook</router-link>
      </div>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
@import "scss/variables.scss";
@import url("https://fonts.googleapis.com/css2?family=Lobster+Two&display=swap");

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
}

body {
  background: $background;
  padding: 0px;
  margin: 0px;
}

.nav {
  background: $navbar_background;
  margin-bottom: 1rem;
}

.nav__title {
  font-family: "Lobster Two", cursive;
  font-size: 1.5rem;
  margin-left: 1rem;
  padding: 0.3rem;
}

a {
  text-decoration: none;
  color: #2c3e50;
}

// #nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
