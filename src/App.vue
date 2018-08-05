<template>
  <div id="app">
    <nav>
      <Tasks/>
    </nav>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
export default {
  name: "app",
  components: {
    Tasks
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 50%;
}
@import url("https://fonts.googleapis.com/css?family=Montserrat");
body {
  background-color: rgb(255, 255, 255);
  font-family: "Montserrat", sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
body,
html {
  margin: 0;
  height: 100%;
}
nav a {
  padding: 10px;
  text-decoration: none;
  background: #fff;
  border-radius: 3px;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin-right: 15px;
  margin-bottom: 15px;
}
</style>
