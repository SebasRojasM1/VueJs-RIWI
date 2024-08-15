<template>
  <div id="app">
    <!-- Pasar la página activa al header -->
    <Header :activePage="activePage" @changePage="setActivePage" />

    <main>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Header from './components/header/Header.vue';

const activePage = ref('profile'); // Página inicial por defecto

function setActivePage(page: string) {
  activePage.value = page;
}
</script>

<style lang="scss" src="./assets/styles/main.scss"></style>