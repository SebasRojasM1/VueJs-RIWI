<template>
    <section class="teams">
      <div class="head-section">
        <h3>Teams</h3>
        <p>⋮</p>
      </div>
  
      <ul>
        <li class="team-item" v-for="team in teams" :key="team.id">
          <div class="team-container">
            <div class="img-team">
              <img :src="team.icon" :alt="team.name">
            </div>
  
            <div class="info-team">
              <p class="team-name"><strong>{{ team.name }}</strong></p>
              <p class="team-number-members">{{ team.members }} Members</p>
            </div>
          </div>
  
          <div class="team-assignation">
            <p :class="team.tag.toLowerCase()"><strong>{{ team.tag }}</strong></p>
          </div>
        </li>
  
        <a href="">View all Teams</a>
      </ul>
    </section>
  </template>