<script setup>
import { RouterLink, RouterView } from "vue-router";
import Navbar from "./components/Navbar.vue";
</script>

<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <RouterView />
  <div class="characters-container">
    <div v-for="character in characters" :key="character.id" class="character">
      <img :src="character.image" :alt="character.name" />
      <h2>{{ character.name }}</h2>
      <p>Status: {{ character.status }}</p>
      <button @click="addToFavorites(character)">Add to Favorites</button>
    </div>
  </div>
  <Footer />
</template>

<script>
import Footer from "./components/Footer.vue";
import Navbar from "./components/Navbar.vue";

export default {
  components: {
    Navbar,
    Footer,
  },
  data() {
    return {
      favorites: [],
      characters: [],
      logo_src: "/public/img/rickandmorty.png",
      app_name: "Rick And Morty",
    };
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then((Response) => Response.json())
      .then((data) => {
        this.characters = data.results;
      });
  },
};
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
  margin-top: 10px;
  padding: 5px 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #2b8c6d;
}

footer {
  margin-top: 50px;
  text-align: center;
}
</style>
