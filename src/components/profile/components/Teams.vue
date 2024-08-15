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


<script setup lang="ts">
  import { ref } from 'vue';
  
  import reactLogo from '../../../assets/images/logos/react.png'
  import figmaLogo from '../../../assets/images/logos/figma.png'
  import twitterLogo from '../../../assets/images/logos/twitter.png'
  import vuejsLogo from '../../../assets/images/logos/vuejs.png'
  import worldLogo from '../../../assets/images/logos/worls.png'
  
 const teams = ref([
  {
    id: 1,
    name: "React Developers",
    members: 72,
    tag: "Developer",
    icon: reactLogo
  },
  {
    id: 2,
    name: "Support Team",
    members: 122,
    tag: "Support",
    icon: worldLogo
  },
  {
    id: 3,
    name: "UI Designer",
    members: 7,
    tag: "Designer",
    icon: figmaLogo
  },
  {
    id: 4,
    name: "Vue.Js Developers",
    members: 289,
    tag: "Developer",
    icon: vuejsLogo
  },
  {
    id: 5,
    name: "Digital Marketing",
    members: 24,
    tag: "Marketing",
    icon: twitterLogo
  }
])
</script>