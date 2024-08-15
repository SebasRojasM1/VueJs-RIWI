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