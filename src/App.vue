<template>
  <div class="app-container">
    <div class="content-wrapper">
      <AppSidebar />
      <div class="main-content">
        <AppNavbar />
        <ChatLayout />
      </div>
    </div>
  </div>
</template>

<script>
import AppNavbar from './components/AppNavbar.vue';
import AppSidebar from './components/AppSidebar.vue';
import ChatLayout from './components/ChatLayout.vue';

export default {
  name: 'App',
  components: {
    AppNavbar,
    AppSidebar,
    ChatLayout
  }
}
</script>

<style>
.app-container {
  display: flex;
  height: 100vh;
  width: 100%;
}

.content-wrapper {
  display: flex;
  flex: 1;
  overflow: hidden;
}

.main-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  background-color: #f5f7fb;
  overflow: hidden;
}
</style>