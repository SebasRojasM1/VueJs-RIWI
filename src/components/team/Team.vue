<template>
    <div class="team-cards">
      <div v-for="team in teams" :key="team.id" class="card team-card" @mouseleave="hideMenu(team.id)">
        <div class="card-header">
          <div class="team-principal">
            <img class="team-icon" :src="team.icon" alt="Team Icon" />
            <h2>{{ team.name }}</h2>
          </div>
  
          <div class="actions">
            <button class="star-button" 
              :class="{ 'favorite': team.isFavorite }" 
              @click="toggleFavorite(team.id)"><i :class="[team.isFavorite ? 'fa-solid fa-star' : 'fa-regular fa-star']"></i></button>
            <button class="menu-button" @click="toggleMenu(team.id)">⋮</button>
  
            
          </div>
        </div>
  
        <p class="description">{{ team.description }}</p>
  
        <div class="team-info">
          <div class="members">
            <img v-for="member in team.members" :key="member.id" :src="member.avatar" class="member-avatar" alt="Member Avatar" />
          </div>
          
          <div class="tags">
            <span v-for="tag in team.tags" :key="tag" class="tag" :class="`tag tag-${tag.toLowerCase()}`">{{ tag }}</span>
          </div>
        </div>
  
  
        <ul v-if="isMenuVisible(team.id)" class="team-options-menu">
          <li @click="editTeam(team.id)">Editar</li>
          <li @click="deleteTeam(team.id)">Eliminar</li>
          <li @click="addMember(team.id)">Agregar Integrante</li>
        </ul>
        
      </div>
    </div>
  </template>