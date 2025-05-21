<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/table">View All Amiibos</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style>
nav {
  padding: 2rem;
  text-align: center;
  background-color: #f8f9fa;
}

nav a {
  margin: 0 1rem;
  color: #2c3e50;
  text-decoration: none;
  font-weight: bold;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s;
}

nav a:hover {
  background-color: #e9ecef;
}

nav a.router-link-active {
  color: #42b883;
}
</style>
