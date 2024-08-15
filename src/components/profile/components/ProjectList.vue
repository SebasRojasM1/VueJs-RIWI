<template>
    <div class="project-table">
      
      <div class="header">
        <h2>Project List</h2>
        <input type="text" placeholder="Search Project" v-model="searchQuery" />
      </div>
  
      <table>
        <thead>
          <tr>
            <th><input type="checkbox" name="" id=""></th>
            <th>Project</th>
            <th>Leader</th>
            <th>Team</th>
            <th>Progress</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="project in filteredProjects" :key="project.id">
            <td><input type="checkbox" /></td>
            
            <td>
              <img :src="project.icon" alt=""> 
              <div class="project-info">
                <h4>{{ project.name }}</h4>
                <p>{{ project.technology }} Project</p>
              </div>
            </td>
  
            <td>{{ project.leader }}</td>
  
            <td>
              <div class="team">
                <img v-for="(member, index) in project.team" :key="index" :src="member.avatar" alt="team member" />
                <span v-if="project.extraMembers">+{{ project.extraMembers }}</span>
              </div>
            </td>
  
            <td>
              <div class="progress">
                <div class="progress-bar" :style="{ width: project.progress + '%' }"></div>
                <span>{{ project.progress }}%</span>
              </div>
            </td>
            
            <td>
              <button>⋮</button>
            </td>
          </tr>
        </tbody>
      </table>
  
  
      <div class="pagination">
        <span>
          Showing {{ (currentPage - 1) * itemsPerPage + 1 }} to
          {{ Math.min(currentPage * itemsPerPage, totalItems) }} of
          {{ totalItems }} entries
        </span>
        
        <div class="pagination-buttons">
          <button @click="previousPage" :disabled="currentPage === 1">&laquo;</button>
          <button v-for="page in totalPages" :key="page" @click="goToPage(page)" :class="{ active: currentPage === page }">
            {{ page }}
          </button>
          <button @click="nextPage" :disabled="currentPage === totalPages">&raquo;</button>
        </div>
      </div>
    </div>
</template>


<script setup lang="ts">
import { ref, computed } from 'vue';

  import male1 from '../../../assets/images/male1.jpg'
  import male2 from '../../../assets/images/male2.jpg'
  import female2 from '../../../assets/images/female2.jpg'
  import female3 from '../../../assets/images/female3.jpg'
  import male4 from '../../../assets/images/male4.jpg'
  import male5 from '../../../assets/images/user.jpg'
  import female5 from '../../../assets/images/female5.jpg'

  import reactLogo from '../../../assets/images/logos/react.png'
  import figmaLogo from '../../../assets/images/logos/figma.png'
  import pythonLogo from '../../../assets/images/logos/python.webp'
  import xamarinLogo from '../../../assets/images/logos/xamarin.png'
  import vuejsLogo from '../../../assets/images/logos/vuejs.png'


const projects = ref([
  {
    id: 1,
    name: 'BGC eCommerce App',
    technology: 'React',
    icon: reactLogo,
    leader: 'Eileen',
    team: [
      { avatar: male1 },
      { avatar: male2 },
      { avatar: female3 },
    ],
    extraMembers: 3,
    progress: 78,
  },
  {
    id: 2,
    name: 'Falcon Logo Design',
    technology: 'Figma',
    icon: figmaLogo,
    leader: 'Owen',
    team: [
      { avatar: female5 },
      { avatar: male4 },
      { avatar: male1 },
    ],
    extraMembers: 0,
    progress: 25,
  },
  {
    id: 3,
    name: 'Dashboard Design',
    technology: 'Vuejs',
    icon: vuejsLogo,
    leader: 'Keith',
    team: [
      { avatar: male5 },
      { avatar: female5 },
      { avatar: male4 },
    ],
    extraMembers: 0,
    progress: 62,
  },
  {
    id: 4,
    name: 'Foodista mobile app',
    technology: 'Xamarin',
    icon: xamarinLogo,
    leader: 'Merline',
    team: [
      { avatar: female5 },
      { avatar: male1 },
      { avatar: male2 },
    ],
    extraMembers: 8,
    progress: 8,
  },
  {
    id: 5,
    name: 'Dojo Email App',
    technology: 'Python',
    icon: pythonLogo,
    leader: 'Harmonia',
    team: [
      { avatar: male5 },
      { avatar: female2 },
      { avatar: female3 },
    ],
    extraMembers: 5,
    progress: 51,
  },{
    id: 6,
    name: 'Python Magic App',
    technology: 'Python',
    icon: pythonLogo,
    leader: 'Harmonia',
    team: [
      { avatar: male5 },
      { avatar: female2 },
      { avatar: male4 },
    ],
    extraMembers: 5,
    progress: 51,
  },
]);

</script>