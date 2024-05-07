<script setup>
import NavBar from "@/components/NavBar.vue";
</script>

<template>
  <NavBar />
  <div class="container">
    <router-view></router-view> <!-- per vedere la view della rotta -->
  </div>

</template>