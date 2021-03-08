<template>
  <div id="app">
    <div id="nav" class="regular">
      <router-link to="/">Home</router-link> |
      <router-link to="/ItemList">Item List</router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
// ----CSS Reset
* {
  padding: 0;
  margin: 0;
}

// ----Font
@import url("https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Open+Sans:wght@400;600&display=swap");

.heading {
  font-family: "Dancing Script", cursive;
  font-size: 50px;
}

.regular {
  font-family: "Open Sans", sans-serif;
}

.bold {
  font-family: "Open Sans", sans-serif;
  font-weight: 600;
}

// ------Element Styling

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  place-items: center;
  background-color: #F2F2F0;
}

#nav {
  padding: 20px;

  a {
    color: #D95555;
    font-size: 18px;
    text-decoration: none;

    &.router-link-exact-active {
      color: #BF3636;
      font-weight: 600;
      font-weight: bold;
      text-decoration: underline;

    }
  }
}
</style>
