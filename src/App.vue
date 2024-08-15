<template>
  <div id="app">
    <!-- Pasar la página activa al header -->
    <Header :activePage="activePage" @changePage="setActivePage" />

    <main>
      <Profile v-if="activePage === 'profile'" />
      <Team v-if="activePage === 'team'" />
      <Project v-if="activePage === 'projects'" />
      <Connections v-if="activePage === 'connections'" />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Header from './components/header/Header.vue';
import Profile from './components/profile/Profile.vue';
import Team from './components/team/Team.vue';
import Project from './components/project/Project.vue';
import Connections from './components/connections/Connections.vue';

const activePage = ref('profile'); // Página inicial por defecto

function setActivePage(page: string) {
  activePage.value = page;
}
</script>

<style lang="scss" src="./assets/styles/main.scss"></style>