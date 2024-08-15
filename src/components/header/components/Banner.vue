<template>
  <div class="banner">
    <img class="banner-image" :src="headerInfo.bannerImage" alt="Banner Image" />

    <div class="profile-info">
      <img class="profile-avatar" :src="headerInfo.avatar" alt="User Avatar" />

      <div class="profile-details">
        <h2>{{ headerInfo.name }}</h2>

        <div class="profile-meta">
          <span><i class="fa-solid fa-palette" style="margin-right: 10px;"></i> {{ headerInfo.role }}</span>
          <span><i class="fa-solid fa-location-dot" style="margin-right: 10px;"></i> {{ headerInfo.location }}</span>
          <span><i class="fa-regular fa-calendar" style="margin-right: 10px;"></i> Joined {{ headerInfo.joinDate }}</span>
        </div>
      </div>

      <button class="connected-button" :class="{ 'connected': isConnected, 'disconnected': !isConnected }" 
        @click="$emit('toggleConnection')">
        <i class="fa-solid fa-user" style="margin-right: 10px;"></i>{{ isConnected ? 'Connected' : 'Connect' }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  headerInfo: Object,
  isConnected: Boolean,
});
</script>

<style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';

.banner {
  .banner-image {
    width: 100%;
    height: 250px;
    object-fit: cover;
    border-radius: $card-border-radius $card-border-radius 0 0;
  }

  .profile-info {
    display: flex;
    align-items: center;
    background: $card-background-color;
    box-shadow: $card-box-shadow;
    border-radius: 0 0 $card-border-radius $card-border-radius;
    padding: 0 16px;
    width: 100%;
    margin: 0;

    .profile-avatar {
      width: 100px;
      height: 100px;
      border-radius: 6%;
      border: 5px solid white;
      margin-right: 16px;
      position: relative;
      bottom: 30px;
      object-fit: cover;
    }

    .profile-details {
      display: flex;
      flex-direction: column;
      align-items: flex-start;

      h2 {
        margin: 5px 0;
        font-size: 24px;
        color: $color-title-text
      }

      .profile-meta {
        display: flex;
        margin-bottom: 20px;

        span {
          margin-right: 16px;
          display: flex;
          align-items: center;
          color: $color-paragraph-text;
        }
      }
    }

    .connected-button {
      background-color: $color-button-principal;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 10px 16px;
      cursor: pointer;
      margin-left: auto;
      transition: 0.3s ease;
    }

    .connected {
      background-color: $color-button-principal;
    }

    .disconnected {
      background-color: $color-button-secundary;
      color: #8278f0;
    }
  }


  @media screen and (max-width: 768px) {
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
  }
}
</style>