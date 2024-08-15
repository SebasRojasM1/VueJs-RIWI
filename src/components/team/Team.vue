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
  import male1 from '../../assets/images/male1.jpg'
  import female1 from '../../assets/images/female1.jpg'
  import male2 from '../../assets/images/male2.jpg'
  import female2 from '../../assets/images/female2.jpg'
  import male3 from '../../assets/images/male3.jpg'
  import female3 from '../../assets/images/female3.jpg'
  import male4 from '../../assets/images/male4.jpg'
  import female4 from '../../assets/images/female3.jpg'
  import male5 from '../../assets/images/user.jpg'
  import female5 from '../../assets/images/female5.jpg'

  import reactLogo from '../../assets/images/logos/react.png'
  import figmaLogo from '../../assets/images/logos/figma.png'
  import calendarLogo from '../../assets/images/logos/google-calendar.webp'
  import vuejsLogo from '../../assets/images/logos/vuejs.png'
  import worldLogo from '../../assets/images/logos/worls.png'
  import adobeXdLogo from '../../assets/images/logos/adobe-xd.png'
  import htmlLogo from '../../assets/images/logos/html.png'

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



const activeMenuId = ref<number | null>(null);

function toggleMenu(teamId: number) {
  activeMenuId.value = activeMenuId.value === teamId ? null : teamId;
}

function hideMenu(teamId: number) {
  if (activeMenuId.value === teamId) {
    activeMenuId.value = null;
  }
}

function isMenuVisible(teamId: number) {
  return activeMenuId.value === teamId;
}

function editTeam(teamId: number) {
  const team = teams.value.find(t => t.id === teamId);
  if (team) {
    const updatedName = prompt("Edit team name:", team.name);
    const updatedDescription = prompt("Edit team description:", team.description);

    if (updatedName && updatedDescription) {
      team.name = updatedName;
      team.description = updatedDescription;
      console.log(`El equipo con ID: ${teamId} ha sido actualizado.`);
    }
  }
}

function deleteTeam(teamId: number) {
  const team = teams.value.find(t => t.id === teamId);
  if (team) {
    const confirmDelete = confirm(`¿Estás seguro de que deseas eliminar el equipo "${team.name}"?`);
    if (confirmDelete) {
      teams.value = teams.value.filter(t => t.id !== teamId);
      console.log(`El equipo con ID: ${teamId} ha sido eliminado.`);
    }
  }
}

function addMember(teamId: number) {
  const team = teams.value.find(t => t.id === teamId);
  if (team) {
    const memberName = prompt("Nombre del nuevo integrante:");
    const memberRole = prompt("Rol del nuevo integrante:");
    const memberAvatar = prompt("URL de la fotografía del integrante:");

    if (memberName && memberRole && memberAvatar) {
      const newMemberId = team.members.length + 1;
      const newMember = { id: newMemberId, name: memberName, role: memberRole, avatar: memberAvatar };
      team.members.push(newMember);
      console.log(`Nuevo integrante agregado al equipo con ID: ${teamId}.`);
    }
  }
}
</script>


<style lang="scss" scoped>
  @import '../../assets/styles/mixins';
  @import '../../assets/styles/variables';
  
  .team-cards{
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    flex-wrap: wrap;

    .team-card {
      @include card;
      max-width: 400px;
      min-width: 400px;
  
    .card-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      
      .team-principal{
        display: flex;
        align-items: center;

        h2{
          font-size: 18px;
        }

        .team-icon {
          width: 24px;
          height: 24px;
          margin-right: 8px;
        }
      }

      .actions {
        display: flex;
        align-items: center;
  
        .star-button, .menu-button {
          background: none;
          border: none;
          cursor: pointer;
          margin-left: 8px;
          font-size: 18px;
          transition: 0.3s ease;


          &.favorite {
            color: gold;
          }
        }
      }
    }
  
    .description {
      margin: 8px 0;
      color: #555;
    }

    .team-info{
      display: flex;
      justify-content: center;
      align-items: center;
      justify-content: space-between;

      .members {
      display: flex;
      margin: 8px 0;
  
        .member-avatar {
          width: 32px;
          height: 32px;
          border-radius: 50%;
          margin-right: 4px;
          border: 2px solid white;

          &:nth-child(2){
            position: relative;
            right: 17px;
          }

          &:nth-child(3){
            position: relative;
            right: 34px;
          }

          &:nth-child(4){
            position: relative;
            right: 51px;
          }

          
          &:nth-child(5){
            position: relative;
            right: 68px;
          }

          
          &:nth-child(6){
            position: relative;
            right: 85px;
          }

          &:nth-child(7){
            position: relative;
            right: 102px;
          }
        }
      }
  
      .tags {
        display: flex;
        margin-top: 8px;
    
        .tag {
          background-color: #e0e0e0;
          border-radius: 6px;
          padding: 5px 9px;
          margin-right: 9px;
          font-size: 13px;
          font-weight: bold;

          &.tag-vuejs, &.tag-email, &.tag-hubilo, &.tag-ui-ux {
            background-color: $green-background-color;
            color: $green-font-color;
          }
          &.tag-developer, &.tag-xd {
            background-color: $red-background-color;
            color: $red-font-color;
          }
          &.tag-react, &.tag-twitter {
            background-color: $purple-background-color;
            color: $purple-font-color;
          }
          &.tag-mui, &.tag-zendesk , &.tag-mui {
            background-color: $blue-background-color;
            color: $blue-font-color;
          }
          &.tag-sketch, &.tag-html{
            background-color: $yellow-background-color;
            color: $yellow-font-color;
          }
          &.tag-figma {
            background-color: $gray-background-color;
            color: $gray-font-color;
          }
        }
      }
    }
  }

  .team-options-menu {
    position: relative;
    left: 0px;
    top: 5px;
    list-style: none;
    padding: 0;
    margin: 0;
    background-color: white;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    z-index: 5;
  }

  .team-options-menu li {
    padding: 10px;
    cursor: pointer;
  }

  .team-options-menu li:hover {
    background-color: #f0f0f0;
  }
}
</style>
  