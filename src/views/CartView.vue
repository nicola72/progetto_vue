<script setup>
  import {ref} from "vue";
  import axios from 'axios';

  const cart = ref([]);

  const url = 'http://localhost:3000/cart';

  axios.get(url).then( response => {
    cart.value = response.data;
  });
</script>

<template>
  <div>
    Carrello
    <div>
      <table class="table">
        <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nome</th>
          <th scope="col">Prezzo</th>
          <th scope="col">Q.tà</th>
          <th scope="col">Totale</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="item in cart" :key="item.id">
          <td>{{item.id}}</td>
          <td>{{item.name}}</td>
          <td>{{item.price}}</td>
          <td>{{item.qty}}</td>
          <td></td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>


</template>

<style scoped>

</style>