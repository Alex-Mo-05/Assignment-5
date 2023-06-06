<script setup>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
import { useStore } from '../store/index.js';
import router from "../router";


const store = useStore();

function openPurchase() {
  router.push("/purchase");
}

</script>

<template>
  <Header />
  <button @click="openPurchase()">Catalog</button>
  <div class="cartBox" v-for="movie in Array.from(store.cart.values())">
    <p>Movie Title: {{ movie.title }}</p>
    <img :src="`https://image.tmdb.org/t/p/w500${movie.poster}`" />
  </div>
  <Footer />
</template>

<style scoped>
:root {
  background-color: rgba(0, 0, 0, 0.856);
}

button {
  font-size: 20px;
  color: rgb(202, 26, 26);
  background-color: rgb(54, 52, 52);
  border-color: rgba(71, 70, 70, 0.76);
  border-width: 3px;
}

.cartBox {
  margin-bottom: 20px;
  font-weight: bold;
  text-align: left;
  color: rgb(202, 26, 26);
  font-size: 20px;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

img {
  width: 250px;
  height: 400px;
}
</style>
