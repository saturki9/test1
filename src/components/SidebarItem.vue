// SidebarItem.vue
<template>
  <div class="sidebar-item" :class="{ active: active }">
    <i :class="icon"></i>
    <span>{{ text }}</span>
    <i v-if="expandable" class="bi bi-chevron-down expand-icon"></i>
  </div>
</template>

<script>
export default {
  name: 'SidebarItem',
  props: {
    icon: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    active: {
      type: Boolean,
      default: false
    },
    expandable: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
.sidebar-item {
  display: flex;
  align-items: center;
  padding: 12px 20px;
  color: #5a6a85;
  cursor: pointer;
  transition: all 0.3s;
}

.sidebar-item:hover {
  background-color: #f5f7fb;
  color: #3377ff;
}

.sidebar-item.active {
  background-color: #eef2ff;
  color: #3377ff;
  border-left: 3px solid #3377ff;
}

.sidebar-item i {
  margin-right: 12px;
  font-size: 18px;
}

.expand-icon {
  margin-left: auto;
  font-size: 12px;
}
</style>