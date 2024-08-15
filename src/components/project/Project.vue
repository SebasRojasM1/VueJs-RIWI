<template>
    <div v-for="project in projects" :key="project.id" class="project-card" @mouseleave="hideMenu(project.id)">
      <div class="card-header">
        <div class="project-head-info">
          <div>
            <img class="icon" :src="project.icon" alt="Project icon">
          </div>
          
          <div>
            <h3>{{ project.name }}</h3>
            <p>Client: {{ project.client }}</p>
          </div>
        </div>
        
        <div class="card-options">
          <button class="options-button" @click="toggleMenu(project.id)">⋮</button>
        </div>
      </div>
      
      <div class="card-body">
        <div class="budget-dates-container">
          <div class="budget">
          <p><strong>{{ project.budget.used }}</strong> / {{ project.budget.total }}</p>
          <p>Total Budget</p>
        </div>

        <div class="dates">
          <p>Start Date: {{ project.startDate }}</p>
          <p>Deadline: {{ project.deadline }}</p>
        </div>
      </div>


        <p class="description">{{ project.description }}</p>
        <hr>
        <div class="hours">
          <p>All Hours: {{ project.hours.completed }} / {{ project.hours.total }}</p>
          <p class="days-left">{{ project.daysLeft }} Days left</p>
        </div>

        <div class="tasks">
          <p>Task: {{ project.tasks.completed }} / {{ project.tasks.total }}</p>
          <p>{{ project.tasks.percentage }}% Completed</p>
        </div>

        <div class="progress-bar">
          <div class="progress" :style="{ width: project.tasks.percentage + '%' }"></div>
        </div>

        <div class="footer">
          <div class="team">
            <img v-for="member in project.team" :key="member.id" :src="member.avatar" alt="Team Member Avatar" class="avatar" />
            <p>{{ project.team.length }} members</p>
          </div>
          
          <div class="comments">
            <p><i class="fa-regular fa-message" style="margin-right: 4px;"></i>{{ project.comments }}</p>
          </div>
        </div>
      </div>


      <ul v-if="isMenuVisible(project.id)" class="project-options-menu">
        <li @click="editProject(project.id)">Editar</li>
        <li @click="deleteProject(project.id)">Eliminar</li>
      </ul>
    </div>
  </template>