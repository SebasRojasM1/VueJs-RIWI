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