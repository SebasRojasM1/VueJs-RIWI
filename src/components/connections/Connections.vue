<template>
    <div v-for="user in users" :key="user.id"  class="connection-card">
      <div class="card-options">
        <button class="options-button">⋮</button>
      </div>
  
      <div class="card-header">
        <img class="avatar" :src="user.avatar" alt="User Avatar" />
      </div>
  
      <div class="card-body">
        <h3>{{ user.name }}</h3>
        <p>{{ user.role }}</p>
  
        <div class="tags">
          <span v-for="tag in user.tags" :key="tag" class="tag" :class="`tag tag-${tag.toLowerCase()}`">{{ tag }}</span>
        </div>
  
        <div class="stats">
          <div class="stat">
            <h4>{{ user.projects }}</h4>
            <p>Projects</p>
          </div>
  
          <div class="stat">
            <h4>{{ user.tasks }}</h4>
            <p>Tasks</p>
          </div>
  
          <div class="stat">
            <h4>{{ user.connections }}</h4>
            <p>Connections</p>
          </div>
        </div>
  
        <div class="actions">
          <button class="connected-button" :class="{ 'connected': user.isConnected, 'disconnected': !user.isConnected }" 
          @click="toggleConnected(user.id)">
            <i :class="[user.isConnected ? 'fa-solid fa-user' : 'fa-regular fa-user']"></i> 
            {{ user.isConnected ? 'Connected' : 'Connect' }}
          </button>
  
          <button class="message-button">
            <i class="fa-regular fa-envelope"></i>
          </button>
        </div>
      </div>
    </div>
  </template>



<script setup lang="ts">
import { ref } from 'vue';
import male1 from "../../assets/images/male1.jpg"
import female1 from "../../assets/images/female1.jpg"
import male2 from "../../assets/images/male2.jpg"
import female2 from "../../assets/images/female2.jpg"
import male3 from "../../assets/images/male3.jpg"
import female3 from "../../assets/images/female3.jpg"

function toggleConnected(userId: number) {
  const user = users.value.find(u => u.id === userId);

  if (user) {
    user.isConnected = !user.isConnected;
  }
}

// Lista de usuarios
const users = ref([
  {
    id: 1,
    name: 'Mark Gilbert',
    role: 'UI Designer',
    avatar: male1,
    tags: ['Figma', 'Sketch'],
    projects: 18,
    tasks: 834,
    connections: 129,
    isConnected: true
  },
  {
    id: 2,
    name: 'Eugenia Parsons',
    role: 'Developer',
    avatar: female1,
    tags: ['Angular', 'React'],
    projects: 112,
    tasks: 2310,
    connections: 1280,
    isConnected: false
  },
  {
    id: 3,
    name: 'Francis Byrd',
    role: 'Developer',
    avatar: male2,
    tags: ['HTML', 'React'],
    projects: 32,
    tasks: 1250,
    connections: 890,
    isConnected: false
  },
  {
    id: 4,
    name: 'Leon Lucas',
    role: 'UI/UX Designer',
    avatar: female2,
    tags: ['Figma', 'Sketch', "Photoshop"],
    projects: 86,
    tasks: 12400,
    connections: 890,
    isConnected: false
  },
  {
    id: 5,
    name: 'Jayden Rogers',
    role: 'Full Stack Developer',
    avatar: male3,
    tags: [ 'React', 'HTML', "NodeJs"],
    projects: 244,
    tasks: 23800,
    connections: 2140,
    isConnected: true
  },
  {
    id: 6,
    name: 'Jeanetter Powell',
    role: 'SEO',
    avatar: female3,
    tags: ['Analysis', 'Writing'],
    projects: 32,
    tasks: 1280,
    connections: 1270,
    isConnected: false
  }
]);

</script>