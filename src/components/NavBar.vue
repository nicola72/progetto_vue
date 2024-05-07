<script setup>
  import axios from "axios";
  import {ref} from 'vue';

  const categories = ref([]);
  const url = 'http://localhost:3000/categories';

  //faccio la chiamata axios all'endpoint http://localhost:3000/categories per prendere le categorie dal server e valorizzo la prop value della const categories
  //axios.get(url).then( function (response) { categories.value = response.data });
  //axios.get(url).then( (response) => { categories.value = response.data });
  axios.get(url).then( response => categories.value = response.data );
</script>
<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Navbar</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <!-- se usassi il tag <a> avrei sempre il refresh della pagina -->
            <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/about">About</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/contatore">Contatore</router-link>
          </li>
          <!-- faccio il ciclo sulle categorie -->
          <li v-for="category in categories" :key="category.id">
            <!-- il to deve avere i  due punti perchè contiene un'espressione javascript al suo interno tramite i backtick posso agganciare la stringa 'categories' con la prop dinamica category.id -->
            <router-link class="nav-link" aria-current="page" :to="`/categories/${category.id}`">{{ category.name }}</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/cart">Carrello</router-link>
          </li>
        </ul>
        <form class="d-flex">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<style scoped>

</style>