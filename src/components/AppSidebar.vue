// Sidebar.vue (renamed to AppSidebar in script)
<template>
  <div class="sidebar">
    <div class="sidebar-header">
      <div class="logo-container">
        <img src="@/assets/LLOGO.png" alt="Logo" class="logo">
        <span class="logo-text">HI TEAM</span>
      </div>
    </div>
    <div class="sidebar-menu">
      <SidebarItem icon="bi bi-grid-1x2-fill" text="Dashboard" active />
      <SidebarItem icon="bi bi-bag" text="Orders" />
      <SidebarItem icon="bi bi-people" text="Passengers" />
      <SidebarItem icon="bi bi-person-badge" text="Captains" />
      <SidebarItem icon="bi bi-list-ul" text="Categories" />
      <div class="separator"></div>
      <SidebarItem icon="bi bi-credit-card" text="Settlement" />
      <SidebarItem icon="bi bi-envelope" text="Contact" />
      <SidebarItem icon="bi bi-star" text="Reviews" />
      <div class="separator"></div>
      <SidebarItem icon="bi bi-shield-lock" text="Permissions" expandable />
      <SidebarItem icon="bi bi-translate" text="Translation" />
      <SidebarItem icon="bi bi-play-btn" text="Education Video" />
      <SidebarItem icon="bi bi-gear" text="Settings" />
      <SidebarItem icon="bi bi-file-earmark-text" text="Content" />
    </div>
  </div>
</template>

<script>
import SidebarItem from './SidebarItem.vue';

export default {
  name: 'AppSidebar', 
  components: {
    SidebarItem
  }
}
</script>

<style scoped>
.sidebar {
  width: 280px;
  background-color: white;
  border-right: 1px solid #eaedf1;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}

.sidebar-item:hover {
  background-color: #635BFF;
  color: #ffffff; /* Change text color on hover */
  border-radius: 20px;
  margin: 10px;
}

.sidebar-item.active {
  background-color: #635BFF;
  color: #ffffff; 
  border-radius: 20px;
  margin: 10px;

}

.sidebar-header {
  padding: 20px 15px;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 12px;
}

.logo {
  height: 60px;
  width: auto; /* Maintain aspect ratio */
  object-fit: contain; /* Ensure logo fits properly */
}

.logo-text {
  font-weight: bold;
  font-size: 18px;
}

.sidebar-menu {
  padding: 15px 0;
}

.separator {
  height: 1px;
  background-color: #eaedf1;
  margin: 15px 20px;
}
</style>