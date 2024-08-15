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


<script setup lang="ts">
  import { ref } from 'vue';
  import male1 from "../assets/images/male1.jpg"
  import female1 from "../assets/images/female1.jpg"
  import male2 from "../assets/images/male2.jpg"
  import female2 from "../assets/images/female2.jpg"
  import male3 from "../assets/images/male3.jpg"
  import female3 from "../assets/images/female3.jpg"
  import male4 from "../assets/images/male4.jpg"
  import female4 from "../assets/images/female3.jpg"
  import male5 from "../assets/images/user.jpg"
  import female5 from "../assets/images/female5.jpg"

  import reactLogo from "../assets/images/logos/react.png"
  import figmaLogo from "../assets/images/logos/figma.png"
  import calendarLogo from "../assets/images/logos/google-calendar.webp"
  import vuejsLogo from "../assets/images/logos/vuejs.png"
  import worldLogo from "../assets/images/logos/worls.png"
  import adobeXdLogo from "../assets/images/logos/adobe-xd.png"
  import htmlLogo from "../assets/images/logos/html.png"

const teams = ref([
  {
    id: 1,
    name: 'React Developers',
    description: 'We don\'t make assumptions about the rest of your technology stack, so you can develop new features in React.',
    icon: reactLogo,
    members: [
      { id: 1, name: 'John Doe', role: 'Developer', avatar: male1 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female1 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female2 }
    ],
    tags: ['React', 'MUI'],
    isFavorite: false,
  },
  {
    id: 2,
    name: 'Vue.js Dev Team',
    description: 'The development of Vue and its ecosystem is guided by international team, some of whom have chosen to be featured below.',
    icon: vuejsLogo,
    members: [
      { id: 1, name: 'John Doe', role: 'Developer', avatar: male3 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female3 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male4 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female4 }
    ],
    tags: ['Vuejs', 'Developer'],
    isFavorite: false,
  },
  {
    id: 3,
    name: 'Creative Designers',
    description: 'A design of product team is more than just the people on it. A team includes the people, the roles they play, and the collaboration they foster.',
    icon: adobeXdLogo,
    members: [
      { id: 1, name: 'John Doe', role: 'Developer', avatar: male5 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female5 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female3 }
    ],
    tags: ['Sketch', 'XD'],
    isFavorite: false,
  },
  {
    id: 4,
    name: 'Support Team',
    description: 'Support your team. Your customer support team is fielding the good, the bad and the ugly day in and day out.',
    icon: worldLogo,
    members: [
    { id: 1, name: 'John Doe', role: 'Developer', avatar: male5 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female5 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female3 }
    ],
    tags: ['Zendesk'],
    isFavorite: false,
  },
  {
    id: 5,
    name: 'Digital Marketing',
    description: 'Digital marketing refers to advertising delivered through digital channels such as search engines, websites, and mobile apps.',
    icon: worldLogo,
    members: [
    { id: 1, name: 'John Doe', role: 'Developer', avatar: male1 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female1 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female2 }
    ],
    tags: ['Twitter', 'Email'],
    isFavorite: false,
  },
  {
    id: 6,
    name: 'Event',
    description: 'Event is defined as a particular contest which is part of a program of constest. An example of an event is the long jump competition',
    icon: calendarLogo,
    members: [
      { id: 1, name: 'John Doe', role: 'Developer', avatar: male5 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female5 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female3 }
    ],
    tags: ['Hubilo'],
    isFavorite: false,
  },
  {
    id: 7,
    name: 'Figma Resources',
    description: 'Explore, install, use, and remiss thousands of plugins and files published of the Figma Community by designers and developers.',
    icon: figmaLogo,
    members: [
      { id: 1, name: 'John Doe', role: 'Developer', avatar: male5 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female5 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female3 }
    ],
    tags: ['UI-UX', 'Figma'],
    isFavorite: false,
  },
  {
    id: 8,
    name: 'Native Mobile App',
    description: 'React native lets you create user friendly native apps and doesn´t compromise your users´ experiences. With it´s robust framework.',
    icon: reactLogo,
    members: [
    { id: 1, name: 'John Doe', role: 'Developer', avatar: male5 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female5 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female3 }
    ],
    tags: ['React'],
    isFavorite: false,
  },
  {
    id: 9,
    name: 'Only Beginners',
    description: 'Learn the basics of how websited work, front-end vs back-end, and using a code editor. Learn basic HTML, CSS and ...',
    icon: htmlLogo,
    members: [
    { id: 1, name: 'John Doe', role: 'Developer', avatar: male1 },
      { id: 2, name: 'Jane Smith', role: 'Designer', avatar: female1 },
      { id: 3, name: 'Sam Johnson', role: 'Tester', avatar: male2 },
      { id: 4, name: 'Sam Johnson', role: 'Tester', avatar: female2 }
    ],
    tags: ['CSS', 'HTML'],
    isFavorite: false,
  }
]);

function toggleFavorite(teamId: number) {
  const team = teams.value.find(t => t.id === teamId);
  if (team) {
    team.isFavorite = !team.isFavorite;
  }
}



</script>