<template>
    <div class="profile-container">
      <Aside />
    </div>
</template>
  
<script setup lang="ts">
  import Aside from './components/Aside.vue';

</script>
  
<style lang="scss" scoped>
  @import '../../assets/styles/mixins';
  @import '../../assets/styles/variables';

  .profile-container{
    display: grid;
    grid-template-columns: repeat(5, 1fr); // 5 columnas iguales
    grid-template-rows: repeat(3, 1fr); // 4 filas iguales
    gap: 20px;
    background-color: $background-color;
  }
</style>