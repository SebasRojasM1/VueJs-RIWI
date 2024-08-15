<template>
  <header class="header">
    <SearchBar :headerInfo="headerInfo" />
    <Banner :headerInfo="headerInfo" :isConnected="isConnected" @toggleConnection="toggleConnection" />
    <NavOptions :activePage="activePage" @changePage="changePage" />
  </header>
</template>

<script setup lang="ts">
import { ref, defineProps, defineEmits } from 'vue';
import SearchBar from './components/SearchBar.vue';
import Banner from './components/Banner.vue';
import NavOptions from './components/NavOptions.vue';
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


// Estado del botón
const isConnected = ref(true);

// Alternar estado del botón
function toggleConnection() {
  isConnected.value = !isConnected.value;
}

/*Logica para traer el cambio de pagina y aplicarle luego los estilos*/
// Recibir la página activa como prop
const props = defineProps({
  activePage: String,
});

const emit = defineEmits(['changePage']);

function changePage(page: string) {
  emit('changePage', page);
}
</script>

<style lang="scss" scoped>
@import '../../assets/styles/variables';
@import '../../assets/styles/mixins';

.header {
  min-width: 100%;

  @media screen and (max-width: 768px) {
    .header{

      .navbar{
        .search-bar{
          input{
            width: 260px;
          }
        }
      }

      .banner{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;

        .profile-info{
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: center;
          padding-bottom: 20px;

          .profile-details{
            display: flex;
            align-items: center;
            justify-content: center
          }
          
          .connected-button{
            margin-left: 0;
          }
        }
      }

      .nav-options{
        display: flex;
        align-items: center;
        justify-content: center;
        margin-right: 0;
      }
    }
  }
}
</style>