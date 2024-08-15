<template>
    <section class="activity-timeline">
      <h3><i class="fa-solid fa-chart-simple" style="margin-right: 13px;"></i>Activity Timeline</h3>
      <ul>
        <li class="timeline-item">
          <div class="item-content">
            <p><strong>12 Invoices have been paid</strong></p>
            <p>Invoices have been paid to the company</p>
            <a href="#" class="document-link">
              <i class="fa-solid fa-file-pdf"></i> invoice.pdf
            </a>
          </div>
          <p class="item-time">12 min ago</p>
        </li>
        <li class="timeline-item">
          <div class="item-content">
            <p><strong>Client Meeting</strong></p>
            <p>Project meeting with John @10:15am</p>
            <div class="user-info">
              <img src="https://www.spokanejournal.com/ext/resources/2024/04/04/KevinPerson_web.jpg?t=1712818920&width=791" alt="User Image" class="user-image">
              <div class="user-details">
                <p>Lester McCarthy (Client)</p>
                <p>CEO of PixInvent</p>
              </div>
            </div>
          </div>
          <p class="item-time">45 min ago</p>
        </li>
        <li class="timeline-item">
          <div class="item-content">
            <p><strong>Create a new project for client</strong></p>
            <p>6 team members in a project</p>
            <div class="team-members">
              <img src="https://cdn-icons-png.freepik.com/512/219/219986.png" alt="Team Member 1" class="team-image">
              <img src="https://cdn-icons-png.freepik.com/512/219/219986.png" alt="Team Member 2" class="team-image">
              <img src="https://cdn-icons-png.freepik.com/512/219/219986.png" alt="Team Member 3" class="team-image">
              <span class="more-members">+3</span>
            </div>
          </div>
          <p class="item-time">2 Days ago</p>
        </li>
      </ul>
    </section>
  </template>


<script setup lang="ts">

</script>


<style lang="scss" scoped>
@import '../../../assets/styles/mixins';
@import '../../../assets/styles/variables';

.activity-timeline {
grid-column: span 4 / span 4; // Ocupa las columnas 2 a 5
grid-row: span 1 / span 1; // Ocupa solo la fila necesaria
background-color: $card-background-color;
border-radius: $card-border-radius;
box-shadow: $card-box-shadow;
padding: 20px;
color: $color-paragraph-text;

h3 {
  color: $color-title-text;
  font-weight: bold;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
}

ul {
  list-style: none;
  padding: 0;

  .timeline-item {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 20px;
    position: relative;

    .item-content {
      max-width: 80%; // Para ajustar el espacio del contenido
      font-size: 0.9rem;
      margin-bottom: 5px;

      strong {
        color: $color-title-text;
      }

      .document-link {
        display: flex;
        align-items: center;
        color: $color-button-principal;
        font-size: 0.9rem;
        margin-top: 5px;
        background-color: #eeeeef;
        padding: 10px;
        border-radius: 5px;
        color: #a8a6ad;
        text-decoration: none;
        width: 110px;
        object-fit: cover;

        i {
          margin-right: 8px;
          color: red;
        }
      }

      .user-info {
        display: flex;
        align-items: center;
        margin-top: 10px;

        .user-image {
          width: 32px;
          height: 32px;
          border-radius: 50%;
          margin-right: 10px;
          object-fit: cover;
        }

        .user-details {
          font-size: 0.85rem;
          color: $color-paragraph-text;
        }
      }

      .team-members {
        display: flex;
        align-items: center;
        margin-top: 10px;

        .team-image {
          width: 32px;
          height: 32px;
          border-radius: 50%;
          margin-right: 5px;
          border: 2px solid white;

          &:nth-child(2){
            position: relative;
            right: 17px;
          }

          &:nth-child(3){
            position: relative;
            right: 32px;
          }
        }

        .more-members {
          @include flex-center;
          padding: 8px;
          border-radius: 50%;
          background-color: $color-button-principal;
          color: $color-button-secundary;
          font-size: 0.85rem;
          font-weight: bold;
          position: relative;
          right: 49px;
          border: 2px solid white;
        }
      }
    }

    .item-time {
      font-size: 0.8rem;
      color: $color-paragraph-text;
      position: absolute;
      right: 0;
      top: 0;
    }
  }
}
}
</style>