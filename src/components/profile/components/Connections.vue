<template>
    <div class="connections">
      <div class="head-section">
        <h3>Connection</h3>
        <p>⋮</p>
      </div>

      <ul>
        <li class="connection-item" v-for="connection in connections" :key="connection.id">
          <div class="item-info">
            <div class="user-container">
              <div class="img-user">
                <img :src="connection.avatar" :alt="connection.name" >
              </div>
              <div class="info-user">
                <p class="item-name"><strong>{{ connection.name }}</strong></p>
                <p class="item-number-users">{{ connection.connections }} Connections</p>
              </div>
            </div>

            <div class="connected-button">
              <button :class="{ connected: connection.IsConnected }">
                <i class="fa-regular fa-user" style="margin-right: 8px;"></i>
              </button>
            </div>
          </div>
        </li>

        <a href="">View all Connections</a>

      </ul>
    </div>
</template>