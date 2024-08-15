<template>
  <div class="navbar">
    <div class="search-bar">
      <input type="text" placeholder="Search ⌘K" />
    </div>

    <div class="user-actions">
      <button class="action-button"><i class="fa-solid fa-arrow-down-a-z"></i></button>
      <button class="action-button"><i class="fa-regular fa-sun"></i></button>
      <button class="action-button"><i class="fa-solid fa-border-all"></i></button>
      <button class="action-button"><i class="fa-regular fa-bell"></i></button>
      <img class="user-avatar" :src="headerInfo.avatar" alt="User Avatar" />
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  headerInfo: Object,
});
</script>

<style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';

.navbar {
  @include flex-center;
  justify-content: space-between;
  padding: 8px 16px;
  background-color: $card-background-color;
  box-shadow: $card-box-shadow;
  margin: 0 0 35px;
  border-radius: 8px;

  .search-bar {
    margin-left: 18px;
    input {
      padding: 10px 8px;
      border-radius: 8px;
      border: none;
      width: 200%;
    }
  }

  .user-actions {
    display: flex;
    align-items: center;

    .action-button {
      background: none;
      border: none;
      margin-left: 8px;
      cursor: pointer;
      font-size: 16px;
    }

    .user-avatar {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      margin-left: 8px;
      object-fit: cover;
      cursor: pointer;
    }
  }

  
@media screen and (max-width: 768px) {
  .header{
      .navbar{
        .search-bar{
          input{
            width: 260px;
          }
        }
      }
    }
  }

}
</style>