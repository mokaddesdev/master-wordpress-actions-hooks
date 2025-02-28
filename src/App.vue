<script setup>
import { RouterView } from "vue-router";
import Header from "./views/Header.vue";
import Footer from "./views/Footer.vue";
</script>

<template>
  <div class="flex flex-col min-h-screen">
   
    <Header />

 
    <main class="flex-grow">
      <RouterView />
    </main>


    <Footer />
  </div>
</template>
