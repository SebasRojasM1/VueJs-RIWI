<template>
    <div class="connections">
      <div class="head-section">
        <h3>Connection</h3>
        <p>⋮</p>
      </div>

      <ul>
        <li class="connection-item" v-for="connection in connections" :key="connection.id">
          <div class="item-info">
            <div class="user-container">
              <div class="img-user">
                <img :src="connection.avatar" :alt="connection.name" >
              </div>
              <div class="info-user">
                <p class="item-name"><strong>{{ connection.name }}</strong></p>
                <p class="item-number-users">{{ connection.connections }} Connections</p>
              </div>
            </div>

            <div class="connected-button">
              <button :class="{ connected: connection.IsConnected }">
                <i class="fa-regular fa-user" style="margin-right: 8px;"></i>
              </button>
            </div>
          </div>
        </li>

        <a href="">View all Connections</a>

      </ul>
    </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue';
  import male1 from '../../../assets/images/male1.jpg'
  import female1 from '../../../assets/images/female1.jpg'
  import male2 from '../../../assets/images/male2.jpg'
  import female2 from '../../../assets/images/female2.jpg'
  import female3 from '../../../assets/images/female3.jpg'


  const connections = ref([
  {
    id: 1,
    name: "Cecilia Payne",
    connections: "45",
    IsConnected: true,
    avatar: female1
  },
  {
    id: 2,
    name: "Curtis Fletcher",
    connections: "1.32k",
    IsConnected: false,
    avatar: male1
  },
  {
    id: 3,
    name: "Alice Stone",
    connections: "125",
    IsConnected: false,
    avatar: female2
  },
  {
    id: 4,
    name: "Darrell Barnes",
    connections: "456",
    IsConnected: true,
    avatar: male2
  },
  {
    id: 5,
    name: "Eugenia Moore",
    connections: "1.2k",
    IsConnected: true,
    avatar: female3
  }
])
</script>



<style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';
  
  .connections {
    grid-column: span 2 / span 2;
    grid-row: span 1 / span 1; // Ocupa solo la fila 3
    grid-column-start: 2; // Comienza en la columna 2
    grid-row-start: 2; // Comienza en la fila 3
    background-color: $card-background-color;
    border-radius: $card-border-radius;
    box-shadow: $card-box-shadow;
    padding: 20px 20px;
    color: $color-paragraph-text;

    .head-section{
      display: flex;
      align-items: center;
      justify-content: space-between;

      h3 {
        color: $color-title-text;
        font-weight: bold;
        margin-left: 10px;
      } 

      p{
        color: $color-title-text;
        font-weight: bold;
        font-size: 21px;
        margin-right: 38px;      
      }
    }
    

    ul {
      list-style: none;
      padding: 0;

      .connection-item {
        margin: 20px 10px;

        .item-info {
          display: flex;
          justify-content: space-between;
          align-items: center;

          img{
            border-radius: 50%;
          }

          .user-container{
            @include flex-center;

            .img-user img{
              width: 40px;
              margin-right: 10px
            }

            .info-user{
              margin: 0;

              .item-name {
                font-weight: bold;
                font-size: 17px;
                margin: 0;
              }

              .item-number-users {
                font-size: 15px;
                margin: 3px 0 0;
                color: $color-paragraph-text;
              }
            }
          }

          .connected-button button{
            background: none;
            margin: 0;
            border: none;
          }

          .connected-button i{
            background-color: $color-button-principal;
            color: white;
            border: none;
            align-items: center;
            text-align: center;
            border-radius: 8px;
            justify-content: center;
            padding: 12px;
            cursor: pointer;
          }

        }
      }
    }

    a{
        @include flex-center;
        text-decoration: none;
        color: $purple-font-color;
        font-weight: 600;
        margin-top: 10px;
        font-size: 17px;
      }
  }
</style>