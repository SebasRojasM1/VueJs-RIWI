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