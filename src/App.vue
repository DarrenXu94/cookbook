<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>-->
    <div class="nav">
      <div class="nav__title">
        <router-link to="/">The Cookbook</router-link>
        <router-link class="btn-primary" to="/create">New Recipie</router-link>
        <!-- <a href class="btn-primary">New Recipie</a> -->
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
  height: 100vh;
}

body {
  background: $background;
  padding: 0px;
  margin: 0px;
}

.nav {
  background: $navbar_background;
  height: 3.5rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.nav__title {
  font-family: "Lobster Two", cursive;
  font-size: 1.5rem;
  margin-left: 1rem;
  padding: 0.3rem;
  display: flex;
  justify-content: space-between;
}

a {
  text-decoration: none;
  color: #2c3e50;
}

.btn-primary {
  display: inline-block;
  padding: 0.15em 0.8em;
  border: 0.1em solid #ffffff;
  border-radius: 0.12em;
  box-sizing: border-box;
  text-decoration: none;
  color: #ffffff;
  text-align: center;
  transition: all 0.2s;
  font-size: 1rem;
}
.btn-primary:hover {
  color: #2c3e50;
  background-color: #ffffff;
}

.btn-secondary {
  display: inline-block;
  padding: 0.15em 0.8em;
  border: 0.1em solid $navbar_background;
  border-radius: 0.12em;
  box-sizing: border-box;
  text-decoration: none;
  color: $navbar_background;
  text-align: center;
  transition: all 0.2s;
  font-size: 1rem;
}
.btn-secondary:hover {
  color: #fff;
  background-color: $navbar_background;
}
</style>
