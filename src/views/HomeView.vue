<template>
  <div class="main-container">
    <h1>Personagens de Rick And Morty</h1>
    <div class="characters-container">
      <div
        v-for="character in characters"
        :key="character.id"
        class="character"
      >
        <img :src="character.image" :alt="character.name" />
        <h2>{{ character.name }}</h2>
        <p>Status: {{ character.status }}</p>
        <p>Gender: {{ character.gender }}</p>

        <button @click="addToFavorites(character)">Add to Favorites</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      characters: [],
      favorites: JSON.parse(localStorage.getItem("favorites")) || [],
    };
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then((Response) => Response.json())
      .then((data) => {
        this.characters = data.results;
      });
  },
  methods: {
    addToFavorites(character) {
      const exists = this.favorites.some((fav) => fav.id === character.id);
      if (!exists) {
        this.favorites.push(character);
        localStorage.setItem("favorites", JSON.stringify(this.favorites));
        alert(`${character.name} added to favorites!`);
      } else {
        alert(`${character.name} is already in favorites.`);
      }
    },
  },
};
</script>
