<template>
  <nav class="navbar">
    <div class="left">
      <button class="search-button">
        <img src="@/assets/icons/search-icon.png" alt="Search" />
      </button>
      <button class="apps-button">
        <img src="@/assets/icons/apps-icon.png" alt="Apps" />
      </button>
    </div>
    <div class="right">
      <button class="theme-toggle">
        <img src="@/assets/icons/theme-icon.png" alt="Theme" />
      </button>
      <button class="notifications">
        <img src="@/assets/icons/notifications-icon.png" alt="Notifications" />
      </button>
      <div class="language-selector">
        <img src="@/assets/icons/language-flag.png" alt="Selected language" />
      </div>
      <div class="user-profile" @click="toggleProfileMenu">
        <img src="@/assets/icons/profile-avatar.png" alt="User avatar" />
        <div class="profile-menu" v-if="showProfileMenu">
          <ul>
            <li>Profile</li>
            <li>Settings</li>
            <li>Logout</li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      showProfileMenu: false
    }
  },
  methods: {
    toggleProfileMenu() {
      this.showProfileMenu = !this.showProfileMenu
    }
  }
}
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 1rem;
  border-bottom: 1px solid #eaeaea;
  background-color: white;
  width: 100%;
}

.left, .right {
  display: flex;
  align-items: center;
}

button {
  background: none;
  border: none;
  cursor: pointer;
  margin: 0 0.5rem;
  padding: 0.5rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

button:hover {
  background-color: #f5f5f5;
}

button img, .language-selector img, .user-profile img {
  width: 20px;
  height: 20px;
  object-fit: contain;
}

.user-profile img {
  width: 32px;
  height: 32px;
  border-radius: 50%;
}

.user-profile {
  position: relative;
  margin-left: 0.5rem;
}

.profile-menu {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: white;
  border: 1px solid #eaeaea;
  border-radius: 4px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  z-index: 100;
}

.profile-menu ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.profile-menu li {
  padding: 0.75rem 1rem;
  cursor: pointer;
}

.profile-menu li:hover {
  background-color: #f5f5f5;
}
</style>