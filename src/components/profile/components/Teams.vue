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


<style lang="scss" scoped>
  @import '../../../assets/styles/mixins';
  @import '../../../assets/styles/variables';
  
  .teams {
    grid-column: span 2 / span 2;
    grid-row: span 1 / span 1; // Ocupa solo la fila 3
    grid-column-start: 4; // Comienza en la columna 4
    grid-row-start: 2; // Comienza en la fila 3
    background-color: $card-background-color;
    border-radius: $card-border-radius;
    box-shadow: $card-box-shadow;
    padding: 20px;
    color: $color-paragraph-text;

    .head-section{
      display: flex;
      align-items: center;
      justify-content: space-between;

      h3 {
        color: $color-title-text;
        font-weight: bold;
        margin-left: 10px;
      } 

      p{
        color: $color-title-text;
        font-weight: bold;
        font-size: 21px;
        margin-right: 38px;      
      }
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;

      .team-item {
        margin: 5px 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;

        .team-container {
          display: flex;
          justify-content: space-between;
          align-items: center;

          .img-team img{
            width: 30px;
            margin-right: 10px
          }

          .info-team{
            margin: 0;

            .team-name {
              font-weight: bold;
              font-size: 17px;
              margin: 0;
            }

            .team-number-members {
                font-size: 15px;
                margin: 3px 0 0;
                color: $color-paragraph-text;
              }
            }
          }

          .team-assignation p{
            padding: 5px 12px;
            text-align: center;
            border-radius: 5px ;
            font-weight: bold;

            &.developer {
              background-color: $red-background-color;
              color: $red-font-color;
            }

            &.support {
              background-color: $purple-background-color;
              color: $purple-font-color;
            }

            &.designer {
              background-color: $blue-background-color;
              color: $blue-font-color;
            }

            &.marketing {
              background-color: $gray-background-color;
              color: $gray-font-color;
            }
          }
        }
      }

      a{
        @include flex-center;
        text-decoration: none;
        color: $purple-font-color;
        font-weight: 600;
        margin-top: 10px;
        font-size: 17px;
      }
    }
</style>