<script setup>
import { RouterLink, RouterView } from "vue-router";
import Navbar from "./components/Navbar.vue";
</script>

<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <RouterView />
  <Footer />
</template>

<script>
export default {
  data() {
    return {
      logo_src: "../public/img/rickandmorty.png",
      app_name: "Rick and Morty Explorer",
    };
  },
};
import Footer from "./components/Footer.vue";
import Navbar from "./components/Navbar.vue";
</script>
<style>
* {
  font-family: Helvetica;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

.characters-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.character {
  margin: 20px;
  text-align: center;
  width: 200px;
}

.character img {
  width: 100%;
  border-radius: 10px;
}

button {
  background-color: #4caf50;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

button:hover {
  background-color: #45a049;
}

footer {
  margin-top: 50px;
  text-align: center;
}
</style>
