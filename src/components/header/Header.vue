<template>
  <header class="header">
    <SearchBar :headerInfo="headerInfo" />

  </header>
</template>

<script setup lang="ts">
import { ref, defineProps, defineEmits } from 'vue';
import SearchBar from './components/SearchBar.vue';
import avatar from "../../assets/images/user.jpg"
import banner from "../../assets/images/banner.jpg"

const headerInfo = ref({
  name: 'John Doe',
  role: 'Coder',
  location: 'Medellin',
  joinDate: 'April 2021',
  avatar: avatar,
  bannerImage: banner,
});

</script>

<style lang="scss" scoped>
@import '../../assets/styles/variables';
@import '../../assets/styles/mixins';

.header {
  min-width: 100%;
}
</style>