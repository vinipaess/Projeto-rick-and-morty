<template>
  <div id="nav">
    <RouterLink to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo" />
    </RouterLink>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">Favoritos</RouterLink>
  </div>
</template>
<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>
<style scoped>
#nav {
  background-color: #222; 
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
#nav #logo-url {
  margin: auto;
  margin-left: 0;
}
#logo {
  width: 50px;
  height: 50px;
}
#nav a {
  color: #00FF00;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}
#nav a:hover {
  color: #fff;
}
</style>
