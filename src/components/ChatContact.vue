// ChatContact.vue
<template>
  <div class="chat-contact">
    <div class="contact-avatar">
      <img :src="contact.avatar" alt="Avatar" />
      <div class="status-indicator" :class="{ 'online': contact.online }"></div>
    </div>
    <div class="contact-info">
      <div class="contact-name">{{ contact.name }}</div>
      <div class="contact-message">{{ contact.message }}</div>
    </div>
    <div class="contact-time">{{ contact.time }}</div>
  </div>
</template>

<script>
export default {
  name: 'ChatContact',
  props: {
    contact: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.chat-contact {
  display: flex;
  align-items: center;
  padding: 12px 15px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.chat-contact:hover {
  background-color: #f5f7fb;
}

.contact-avatar {
  position: relative;
  margin-right: 12px;
}

.contact-avatar img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.status-indicator {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: #ccc;
  border: 2px solid white;
}

.status-indicator.online {
  background-color: #5cb85c;
}

.contact-info {
  flex: 1;
  min-width: 0;
}

.contact-name {
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.contact-message {
  font-size: 12px;
  color: #6c757d;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.contact-time {
  font-size: 11px;
  color: #6c757d;
  white-space: nowrap;
}
</style>