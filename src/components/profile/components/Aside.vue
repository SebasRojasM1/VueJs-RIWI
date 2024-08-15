<template>
    <aside class="aside">
      <!-- About Section -->
      <section class="about">
        <div class="about-info">
          <h3>About</h3>
          <p><i class="fa-regular fa-user" style="margin-right: 13px;"></i><strong>Full Name:</strong> John Doe</p>
          <p><i class="fa-solid fa-check" style="margin-right: 12px;"></i><strong>Status:</strong> Active</p>
          <p><i class="fa-solid fa-crown" style="margin-right: 10px;"></i><strong>Role:</strong> Developer</p>
          <p><i class="fa-regular fa-flag" style="margin-right: 15px;"></i><strong>Country:</strong> COL</p>
          <p><i class="fa-solid fa-arrow-down-a-z" style="margin-right: 12px;"></i><strong>Language:</strong> English</p>
        </div>
  
        <div class="contact-info">
          <h4>Contacts</h4>
          <p><i class="fa-solid fa-phone" style="margin-right: 11px;"></i><strong>Contact:</strong> +123 456 7890</p>
          <p><i class="fa-regular fa-comments" style="margin-right: 8px;"></i><strong>Skype:</strong> john.doe</p>
          <p><i class="fa-regular fa-envelope" style="margin-right: 13px;"></i><strong>Email:</strong> john.doe@example.com</p>
        </div>
  
        <div class="teams-info">
          <h4>Teams</h4>
          <p>Backend Developer (126 Members)</p>
          <p>VueJS Developer (98 Members)</p>
        </div>
      </section>
  
      <!-- Overview Section -->
      <div class="overview">
        <h3>Overview</h3>
        <p><i class="fa-solid fa-check" style="margin-right: 13px;"></i><strong>Task Completed:</strong> 13.5k</p>
        <p><i class="fa-solid fa-users" style="margin-right: 8px;"></i><strong>Connections:</strong> 897</p>
        <p><i class="fa-solid fa-border-all" style="margin-right: 13px;"></i><strong>Projects Completed:</strong> 148</p>
      </div>
    </aside>
</template>
  
  <script setup lang="ts">
  </script>
  
  <style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';
  
.aside {
  grid-row: span 4 / span 4; // Ocupa todas las filas
  grid-column: span 1 / span 1; // Ocupa la primera columna
  display: flex;
  flex-direction: column;
  gap: 20px;

  .about,
  .overview {
    background-color: $card-background-color;
    border-radius: $card-border-radius;
    box-shadow: $card-box-shadow;
    padding: 20px;
    color: $color-paragraph-text;

    h3 {
      color: $color-title-text;
      font-weight: bold;
      margin-bottom: 10px;
    }

    h4 {
      margin-top: 15px;
      font-weight: bold;
      color: $color-title-text;
    }
  }
}
  </style>