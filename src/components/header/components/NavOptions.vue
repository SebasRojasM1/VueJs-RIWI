<template>
  <section class="nav-options">
    <button :class="{ active: activePage === 'profile' }" @click="changePage('profile')">
      <i class="fa-regular fa-user"></i> Profile
    </button>
    <button :class="{ active: activePage === 'team' }" @click="changePage('team')">
      <i class="fa-solid fa-user-group"></i> Team
    </button>
    <button :class="{ active: activePage === 'projects' }" @click="changePage('projects')">
      <i class="fa-solid fa-border-all"></i> Projects
    </button>
    <button :class="{ active: activePage === 'connections' }" @click="changePage('connections')">
      <i class="fa-solid fa-link"></i> Connections
    </button>
  </section>
</template>

<script setup lang="ts">
const props = defineProps({
  activePage: String,
});

const emit = defineEmits(['changePage']);

function changePage(page: string) {
  emit('changePage', page);
}
</script>

<style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';

.nav-options {
  display: flex;
  align-items: center;
  margin: 20px 25px 20px 0;

  button {
    margin: 0 8px;
    color: $color-title-text;
    padding: 10px 25px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;

    i {
      margin-right: 8px;
    }

    &.active {
      background-color: $color-button-principal;
      color: white;
    }
  }

  @media screen and (max-width: 768px) {
    .nav-options{
      @include flex-center;
      margin-right: 0;
    }
  }
}
</style>