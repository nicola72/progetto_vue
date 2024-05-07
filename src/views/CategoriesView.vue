<script setup>
import {watch, ref} from "vue";
import {useRoute} from "vue-router";
import axios from "axios";

const route = useRoute();
//console.log(route)
//const id = route.params.id;
//console.log(id); //in questo modo lo vedrei solo una volta cioè al caricamento del componente CategoryView

const id = ref(null);
const products = ref([]); //la const dei prodotti che inizia come array vuoto poi verrà popolata con la chiamata asincrona axios al server

watch(
    () => route.params.id,
      (id) => {
        const url = 'http://localhost:3000/products?category_id='+id
        axios.get(url).then(response => {
          products.value = response.data;
        })
});

</script>

<template>
  Categorie {{id}}
  <hr />
  <div class="d-flex flex-wrap justify-content-between">
    <div v-for="product in products" :key="product.id" class="card" style="width: 18rem;">
      <img :src="product.image" class="card-img-top" :alt="product.title">
      <div class="card-body">
        <h5 class="card-title">{{product.title}}</h5>
        <p class="card-text">{{product.description.substring(0,100)}}</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>