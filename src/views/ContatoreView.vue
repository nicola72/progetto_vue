<script setup>
import { ref } from 'vue';

// ref per rendere la variabile reattiva, inoltre a questo punto contatore
// diventa un oggetto non più una varaibile di tipo primitivo quindi si può usare const invece di let
const contatore = ref(90);
const incrementa = () =>{
  contatore.value++;
}

const decrementa = () =>{
  contatore.value--;
}
</script>

<template>
  <h1>{{ contatore }}</h1>
  <button @click="decrementa">-</button>
  <button v-on:click="incrementa">+</button>
</template>

