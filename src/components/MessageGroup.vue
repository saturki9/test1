// MessageGroup.vue
<template>
  <div class="message-group" :class="{ 'own-message': group.sender === 'me' }">
    <div v-if="group.sender !== 'me'" class="sender-info">
      <img :src="group.avatar" class="sender-avatar" />
      <div class="sender-name-time">
        <span class="sender-name">{{ group.sender }}</span>
        <span class="message-time">{{ group.time }}</span>
      </div>
    </div>
    <div class="messages" :class="{ 'own-messages': group.sender === 'me' }">
      <div v-for="(message, index) in group.messages" :key="index" class="message-bubble">
        <div v-if="message.text" class="text-message">{{ message.text }}</div>
        <div v-if="message.image" class="image-message">
          <img :src="message.image" alt="Message image" />
        </div>
      </div>
    </div>
    <div v-if="group.sender === 'me'" class="message-time own-time">{{ group.time }}</div>
  </div>
</template>

<script>
export default {
  name: 'MessageGroup',
  props: {
    group: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.message-group {
  margin-bottom: 20px;
}

.sender-info {
  display: flex;
  align-items: center;
  margin-bottom: 8px;
}

.sender-avatar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-right: 10px;
}

.sender-name {
  font-weight: 600;
  margin-right: 10px;
}

.message-time {
  font-size: 12px;
  color: #6c757d;
}

.messages {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 5px;
  max-width: 80%;
}

.own-messages {
  align-items: flex-end;
  margin-left: auto;
}

.message-bubble {
  border-radius: 0px;
  overflow: hidden;
}

.text-message {
  background-color: #e9ecef;
  padding: 10px 15px;
  border-radius: 0px;
  font-size: 14px;
}

.own-message .text-message {
  background-color: #ECFDFD;
  color: #000000;
}

.image-message img {
  max-width: 100%;
  border-radius: 0px;
}

.own-time {
  text-align: right;
  margin-top: 5px;
}
</style>