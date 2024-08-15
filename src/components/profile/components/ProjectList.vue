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