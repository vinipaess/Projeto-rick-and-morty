<template>
  <div class="main-container" />
  <h1>Favoritos</h1>
  <div v-if="favorites.length > 0" class="favorites-container">
    <div
      v-for="favorite in favorites"
      :key="favorite.id"
      class="favorite-character"
    >
      <img :src="favorite.image" :alt="favorite.name" />
      <h2>{{ favorite.name }}</h2>
      <p>Status: {{ favorite.status }}</p>
      <p>Gender: {{ favorite.gender }}</p>
      <button @click="removeFromFavorites(favorite.id)">
        Remove from Favorites
      </button>
    </div>
  </div>
  <div v-else>
    <p>No favorites added yet.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      favorites: JSON.parse(localStorage.getItem("favorites")) || [],
    };
  },
  name: "FavoritesView",
  methods: {
    removeFromFavorites(id) {
      const exists = this.favorites.some((fav) => fav.id === id);
      if (exists) {
        this.favorites = this.favorites.filter((fav) => fav.id !== id);
        localStorage.setItem("favorites", JSON.stringify(this.favorites)); 
      }
    },
  },
};
</script>

<style scoped>
.favorites-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.favorite-character {
  border: 1px solid #ddd;
  border-radius: 8px;
  margin: 10px;
  padding: 10px;
  width: 200px;
  text-align: center;
}

.favorite-character img {
  max-width: 100%;
  border-radius: 8px;
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
</style>
