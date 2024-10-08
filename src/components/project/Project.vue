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
  import worldLogo from '../../assets/images/logos/worls.png'
  import adobeXdLogo from '../../assets/images/logos/adobe-xd.png'
  import htmlLogo from '../../assets/images/logos/html.png'


    const activeMenuId = ref<number | null>(null);

    function toggleMenu(projectId: number) {
    activeMenuId.value = activeMenuId.value === projectId ? null : projectId;
    }

    function hideMenu(projectId: number) {
    if (activeMenuId.value === projectId) {
        activeMenuId.value = null;
    }
    }

    function isMenuVisible(projectId: number) {
    return activeMenuId.value === projectId;
    }

    function editProject(projectId: number) {
    const project = projects.value.find(p => p.id === projectId);
    if (project) {
        const updatedTask = prompt("Edit task done:", project.tasks.completed);
        const updatedPercentage = prompt("Edit project percentage:", project.tasks.percentage);

        if (updatedTask && updatedPercentage) {
        project.tasks.completed = updatedTask;
        project.tasks.percentage = updatedPercentage;
        console.log(`El equipo con ID: ${projectId} ha sido actualizado.`);
        }
    }
    }

    function deleteProject(projectId: number) {
    const project = projects.value.find(t => t.id === projectId);
    if (project) {
        const confirmDelete = confirm(`¿Estás seguro de que deseas eliminar el proyecto "${project.name}"?`);
        
        if (confirmDelete) {
        projects.value = projects.value.filter(t => t.id !== projectId);
        console.log(`El proyecto con ID: ${projectId} ha sido eliminado.`);
        }
    }
    }


  const projects = ref([
    {
    id: 1,
    name: 'Social Banners',
    icon: worldLogo,
    client: 'Christian Jimenez',
    budget: {
      used: '$24.8k',
      total: '$18.2k'
    },
    startDate: '14/2/21',
    deadline: '28/2/22',
    description: 'We are Consulting, Software Development and Web Development Services.',
    hours: {
      completed: 380,
      total: 244
    },
    daysLeft: 28,
    tasks: {
      completed: "290",
      total: 344,
      percentage: "95"
    },
    team: [
      { id: 1, avatar: male1 },
      { id: 2, avatar: female1 },
      { id: 3, avatar: male2 }
    ],
    comments: 15
  },
  {
    id: 2,
    name: 'Admin template',
    icon: reactLogo,
    client: 'Jeffrey Phillips',
    budget: {
      used: '$2.4k',
      total: '$1.8k'
    },
    startDate: '18/8/21',
    deadline: '21/6/22',
    description: 'Time is our most baulable asset, that´s why we want to help you save it by creating...',
    hours: {
      completed: 98,
      total: 135
    },
    daysLeft: 15,
    tasks: {
      completed: "12",
      total: 90,
      percentage: "42"
    },
    team: [
      { id: 1, avatar: male4 },
      { id: 2, avatar: female4 },
      { id: 3, avatar: male5 }
    ],
    comments: 236
  },
  {
    id: 3,
    name: 'App Design',
    icon: reactLogo,
    client: 'Ricky McDonald',
    budget: {
      used: '$980',
      total: '$420'
    },
    startDate: '14/7/21',
    deadline: '8/10/21',
    description: 'App design combines the user interface (UI) and user experience (UX).',
    hours: {
      completed: 880,
      total: 421
    },
    daysLeft: 45,
    tasks: {
      completed: "22",
      total: 140,
      percentage: "68"
    },
    team: [
      { id: 1, avatar: female2 },
      { id: 2, avatar: male3 },
      { id: 3, avatar: female5 }
    ],
    comments: 98
  },
  {
    id: 4,
    name: 'Create Website',
    icon: htmlLogo,
    client: 'Hulda Wright',
    budget: {
      used: '$24.8k',
      total: '$18.2k'
    },
    startDate: '14/2/21',
    deadline: '28/2/22',
    description: 'We are Consulting, Software Development and Web Development Services.',
    hours: {
      completed: 380,
      total: 244
    },
    daysLeft: 28,
    tasks: {
      completed: "290",
      total: 344,
      percentage: "95"
    },
    team: [
      { id: 1, avatar: female2 },
      { id: 2, avatar: male3 },
      { id: 3, avatar: female3 }
    ],
    comments: 15
  },
  {
    id: 5,
    name: 'Figma Dashboard',
    icon: figmaLogo,
    client: 'Jerry Greene',
    budget: {
      used: '$52.7k',
      total: '$28.4k'
    },
    startDate: '12/12/20',
    deadline: '25/12/21',
    description: 'Time is our most baulable asset, that´s why we want to help you save it by creating...',
    hours: {
      completed: 98,
      total: 135
    },
    daysLeft: 15,
    tasks: {
      completed: "12",
      total: 90,
      percentage: "42"
    },
    team: [
      { id: 1, avatar: male1 },
      { id: 2, avatar: female1 },
      { id: 3, avatar: male2 }
    ],
    comments: 236
  },
  {
    id: 6,
    name: 'Logo Design',
    icon: adobeXdLogo,
    client: 'Olive Strickland',
    budget: {
      used: '$980',
      total: '$420'
    },
    startDate: '14/7/21',
    deadline: '8/10/21',
    description: 'App design combines the user interface (UI) and user experience (UX).',
    hours: {
      completed: 880,
      total: 421
    },
    daysLeft: 45,
    tasks: {
      completed: "22",
      total: 140,
      percentage: "68"
    },
    team: [
      { id: 1, avatar: male4 },
      { id: 2, avatar: female5 },
      { id: 3, avatar: male5 }
    ],
    comments: 98
  },
  {
    id: 7,
    name: 'Create Website',
    icon: htmlLogo,
    client: 'Hulda Wright',
    budget: {
      used: '$8.5k',
      total: '$2.43k'
    },
    startDate: '10/2/19',
    deadline: '12/9/22',
    description: 'Your domain name should reflect products or services so that your...',
    hours: {
      completed: 1200,
      total: 820
    },
    daysLeft: 126,
    tasks: {
      completed: "237",
      total: 820,
      percentage: "72"
    },
    team: [
      { id: 1, avatar: male4 },
      { id: 2, avatar: female4 },
      { id: 3, avatar: male5 }
    ],
    comments: 120
  },
  {
    id: 8,
    name: 'Figma Dashboard',
    icon: figmaLogo,
    client: 'Jerry Greene',
    budget: {
      used: '$52.7k',
      total: '$28.4k'
    },
    startDate: '12/12/20',
    deadline: '25/12/21',
    description: 'Use this template to organize your design project. Some of the key features are...',
    hours: {
      completed: 142,
      total: 420
    },
    daysLeft: 5,
    tasks: {
      completed: "29",
      total: 285,
      percentage: "35"
    },
    team: [
      { id: 1, avatar: female2 },
      { id: 2, avatar: male3 },
      { id: 3, avatar: female3 }
    ],
    comments: 20
  },
  {
    id: 9,
    name: 'Logo Design',
    icon: adobeXdLogo,
    client: 'Olive Strickland',
    budget: {
      used: '$1.3k',
      total: '$655'
    },
    startDate: '17/8/21',
    deadline: '02/11/21',
    description: 'Premium logo designs created by top logo designers. Create the branding of business.',
    hours: {
      completed: 580,
      total: 445
    },
    daysLeft: 4,
    tasks: {
      completed: "29",
      total: 290,
      percentage: "100"
    },
    team: [
      { id: 1, avatar: male1 },
      { id: 2, avatar: female1 },
      { id: 3, avatar: male2 }
    ],
    comments: 16
  }
]);
</script>



<style lang="scss" scoped>
@import '../../assets/styles/mixins';
@import '../../assets/styles/variables';
  

.project-card {
  background-color: $card-background-color;
  box-shadow: $card-box-shadow;
  border-radius: $card-border-radius;
  overflow: hidden;
  width: 400px;
  margin: 16px;
  padding: 24px;

  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 16px;

    .project-head-info {
      display: flex;
      align-items: center;
      justify-content: space-between;

      h3 {
        margin: 0;
        font-size: 18px;
        color: $color-title-text;
      }

      p {
        margin: 0;
        color: $color-paragraph-text;
      }

      img{
        width: 26px;
        margin-right: 10px;
      }
    }

    .card-options {
      .options-button {
        background: none;
        border: none;
        cursor: pointer;
        font-size: 24px;
        color: $color-title-text;
      }
    }
  }

  .card-body {

    .budget-dates-container{
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 0;
      padding: 6px 0;

      .budget{
        display: flex;
        flex-direction: column;
        background-color: #f3f3f3;
        border-radius: 8px;
        margin: 0;
        padding: 10px;

        p{
          margin: 0;
          padding: 0;
        }

        p{
          margin: 0;
          padding: 0;
        }
      }

      .dates{
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
        padding: 0;
      }
    }

    .hours{
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 6px 0 8px;
      color: $color-paragraph-text;

      .days-left {
        background-color: $green-background-color;
        color: $green-font-color;
        font-weight: bold;
        font-size: 13px;
        padding: 4px 8px;
        border-radius: 4px;
      }
    }

    .tasks {
      display: flex;
      justify-content: space-between;
      margin: 8px 0 12px;

      p {
        margin: 0;
        color: $color-paragraph-text;
        font-size: 14px;
      }
    }

    .dates {
      display: flex;
      justify-content: space-between;
      margin: 1px 0;

      p {
        margin: 0;
        color: $color-paragraph-text;
      }
    }

    .description {
      color: $color-paragraph-text;
      margin: 8px 0 24px;
    }

    .progress-bar {
      background-color: $gray-background-color;
      border-radius: 8px;
      height: 8px;
      margin: 16px 0;
      overflow: hidden;

      .progress {
        background-color: $color-button-principal;
        height: 100%;
      }
    }

    .footer {
      display: flex;
      justify-content: space-between;
      align-items: center;

      .team {
        display: flex;
        align-items: center;

        .avatar {
          width: 30px;
          border-radius: 50%;
          border: 2px solid $card-background-color;
          margin-right: 4px;

          &:nth-child(2){
            position: relative;
            right: 17px;
          }

          &:nth-child(3){
            position: relative;
            right: 32px;
          }
        }

        p {
          margin: 0;
          color: $color-paragraph-text;
        }
      }

      .comments {
        p {
          margin: 0;
          color: $color-paragraph-text;
        }
      }
    }
  }

.project-options-menu {
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

.project-options-menu li {
  padding: 10px;
  cursor: pointer;
}

.project-options-menu li:hover {
  background-color: #f0f0f0;
}
}
</style>
