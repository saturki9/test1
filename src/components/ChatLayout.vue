<template>
  <div class="chat-layout">
    <div class="chat-header">
      <div class="chat-title">Chat</div>
      <div class="header-actions">
        <button class="btn home-btn">
          <i class="bi bi-house"></i>
        </button>
        <span class="separator">/</span>
        <button class="btn chat-btn active">Chat</button>
      </div>
    </div>
    <div class="chat-container">
      <div class="chat-sidebar">
        <div class="profile-header">
          <div class="profile-info">
            <img :src="activeProfile.avatar" class="profile-avatar" />
            <div class="profile-details">
              <div class="profile-name">{{ activeProfile.name }}</div>
              <div class="profile-role">{{ activeProfile.role }}</div>
            </div>
          </div>
          <button class="options-btn">
            <i class="bi bi-three-dots-vertical"></i>
          </button>
        </div>
        
        <div class="search-container">
          <div class="search-box">
            <i class="bi bi-search"></i>
            <input type="text" placeholder="Search contacts" />
          </div>
        </div>
        <div class="chats-header">
          <span>Recent Chats</span>
          <i class="bi bi-chevron-down"></i>
        </div>
        <div class="chats-list">
  <ChatContact 
    v-for="(contact, index) in contacts" 
    :key="index" 
    :contact="contact" 
    :class="{ 'active': contact.isActive }" 
  />
</div>

      </div>
      <div class="chat-main">
        <div class="chat-header-bar">
          <div class="chat-user-info">
            <img :src="activeChat.avatar" class="chat-user-avatar" />
            <div class="chat-status">
              <span>{{ activeChat.status }}</span>
            </div>
          </div>
          <div class="chat-actions">
            <button class="icon-btn"><i class="bi bi-slash-circle"></i></button>
            <button class="icon-btn"><i class="bi bi-trash"></i></button>
            <button class="icon-btn"><i class="bi bi-telephone"></i></button>
            <button class="icon-btn"><i class="bi bi-camera-video"></i></button>
            <button class="icon-btn"><i class="bi bi-list"></i></button>
          </div>
        </div>
        <div class="chat-content-wrapper">
          <div class="messages-container">
            <MessageGroup v-for="(group, index) in messageGroups" 
                        :key="index" 
                        :group="group" />
          </div>
          <div class="media-preview">
            <div class="media-section">
              <h4>Media (36)</h4>
              <div class="media-grid">
                <div v-for="(media, index) in mediaItems.slice(0, 6)" :key="index" class="media-item">
                  <img :src="media.thumbnail" alt="Media thumbnail" />
                </div>
              </div>
            </div>
            <div class="files-section">
              <h4>Files (36)</h4>
              <div class="files-list">
                <FileItem v-for="(file, index) in files" :key="index" :file="file" />
              </div>
            </div>
          </div>
        </div>
        <div class="message-input-container">
          <div class="message-input">
            <button class="emoji-btn">
              <i class="bi bi-emoji-smile"></i>
            </button>
            <input type="text" placeholder="Type a Message" />
            <div class="input-actions">
              <button class="attach-btn"><i class="bi bi-paperclip"></i></button>
              <button class="mic-btn"><i class="bi bi-mic"></i></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ChatContact from './ChatContact.vue';
import MessageGroup from './MessageGroup.vue';
import FileItem from './FileItem.vue';

export default {
  name: 'ChatLayout',
  components: {
    ChatContact,
    MessageGroup,
    FileItem
  },
  data() {
    return {
      activeProfile: {
        name: 'Mathew Anderson',
        role: 'Marketing Director',
        avatar: require('@/assets/avatars/mathew.png')
      },
      activeChat: {
        avatar: require('@/assets/avatars/andrew.png'),
        status: 'Away'
      },
      contacts: [
        {
          name: 'Michell Flintoff',
          avatar: require('@/assets/avatars/michell.png'),
          message: 'Your Yesterday was great...',
          time: '15 minutes',
          online: true,
          isActive: true
        },
        {
          name: 'Bianca Anderson',
          avatar: require('@/assets/avatars/bianca.png'),
          message: 'Nice looking dress you...',
          time: '30 minutes',
          online: true
        },
        {
          name: 'Andrew Johnson',
          avatar: require('@/assets/avatars/andrew.png'),
          message: 'Sent a photo',
          time: '2 hours',
          online: true
        },
        {
          name: 'Mark Strokes',
          avatar: require('@/assets/avatars/mark.png'),
          message: 'Lorem ipsum text aud...',
          time: '5 days',
          online: true
        },
        {
          name: 'Mark, Stoinus & Rish...',
          avatar: require('@/assets/avatars/group.png'),
          message: 'Lorem ipsum text...',
          time: '5 days',
          online: true
        },
        {
          name: 'Bianca Anderson',
          avatar: require('@/assets/avatars/bianca.png'),
          message: 'Nice looking dress you...',
          time: '30 minutes',
          online: true
        }
      ],
      messageGroups: [
        {
          sender: 'Andrew',
          avatar: require('@/assets/avatars/andrew.png'),
          time: '2 hours ago',
          messages: [
            { text: 'If I don\'t like something, I\'ll stay away from it.' }
          ]
        },
        {
          sender: 'me',
          time: '2 hours ago',
          messages: [
            { text: 'If I don\'t like something, I\'ll stay away from it.' }
          ]
        },
        {
          sender: 'Andrew',
          avatar: require('@/assets/avatars/andrew.png'),
          time: '2 hours ago',
          messages: [
            { text: 'I want more detailed information.' }
          ]
        },
        {
          sender: 'me',
          time: '2 hours ago',
          messages: [
            { text: 'If I don\'t like something, I\'ll stay away from it.' },
            { text: 'They got there early, and they got really good seats.' }
          ]
        },
        {
          sender: 'Andrew',
          avatar: require('@/assets/avatars/andrew.png'),
          time: '2 hours ago',
          messages: [
            { image: require('@/assets/media/bubble.jpg') }
          ]
        }
      ],
      mediaItems: [
        { thumbnail: require('@/assets/media/bubble.jpg') },
        { thumbnail: require('@/assets/media/abstract1.jpg') },
        { thumbnail: require('@/assets/media/abstract2.jpg') },
        { thumbnail: require('@/assets/media/abstract3.jpg') },
        { thumbnail: require('@/assets/media/bubble2.jpg') },
        { thumbnail: require('@/assets/media/abstract4.jpg') }
      ],
      files: [
        {
          name: 'service-task.pdf',
          icon: 'pdf',
          size: '2 MB',
          date: '2 Dec 2022'
        },
        {
          name: 'homepage-design.fig',
          icon: 'fig',
          size: '2 MB',
          date: '2 Dec 2022'
        },
        {
          name: 'about-us.html',
          icon: 'html',
          size: '2 MB',
          date: '2 Dec 2022'
        },
        {
          name: 'work-project.zip',
          icon: 'zip',
          size: '2 MB',
          date: '2 Dec 2022'
        },
        {
          name: 'custom.js',
          icon: 'js',
          size: '2 MB',
          date: '2 Dec 2022'
        }
      ]
    }
  }
}
</script>

<style scoped>
.chat-layout {
  display: flex;
  flex-direction: column;
  height: 100%;
  background-color: white;
  border-right: 1px solid #000000;
}

.chat-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: white;
  border-bottom: 1px solid #eaedf1;
}

.chat-title {
  font-size: 20px;
  font-weight: 600;
}

.header-actions {
  display: flex;
  align-items: center;
}

.btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 6px 12px;
  border-radius: 4px;
}

.btn.active {
  background-color: #e9ecef;
}

.separator {
  margin: 0 10px;
  color: #999;
}

.chat-container {
  display: flex;
  flex: 1;
  overflow: hidden;
}

.chat-sidebar {
  width: 340px;
  background-color: white;
  border-right: 1px solid #eaedf1;
  display: flex;
  flex-direction: column;
}

.profile-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  border-bottom: 1px solid #eaedf1;
}

.profile-info {
  display: flex;
  align-items: center;
}

.profile-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
  margin-right: 10px;
}

.profile-name {
  font-weight: 600;
  font-size: 14px;
}

.profile-role {
  font-size: 12px;
  color: #6c757d;
}

.options-btn {
  background: none;
  border: none;
  color: #6c757d;
  cursor: pointer;
}

.search-container {
  padding: 15px;
}

.search-box {
  display: flex;
  align-items: center;
  background-color: #f5f7fb;
  border-radius: 4px;
  padding: 8px 12px;
}

.search-box i {
  color: #6c757d;
  margin-right: 8px;
}

.search-box input {
  background: none;
  border: none;
  outline: none;
  width: 100%;
  font-size: 14px;
}

.chats-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 15px;
  color: #7d776c;
  font-size: 14px;
}

.chats-list {
  flex: 1;
  overflow-y: auto;
}
.chat-list.active {
  background-color: #1c69c8;  /* or any color you prefer */
  border-left: 3px solid #635BFF;  /* optional: adds a colored border */
}

.chat-main {
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.chat-header-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background-color: white;
  border-bottom: 1px solid #eaedf1;
}

.chat-user-info {
  display: flex;
  align-items: center;
  position: relative;
}

.chat-user-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.chat-status {
  position: absolute;
  bottom: 0;
  right: 0;
  background-color: #5cb85c;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 2px solid white;
}

.chat-actions {
  display: flex;
}

.icon-btn {
  background: none;
  border: none;
  color: #6c757d;
  font-size: 16px;
  padding: 8px;
  cursor: pointer;
}

/* This is the new wrapper to organize messages and media side by side */
.chat-content-wrapper {
  display: flex;
  flex: 1;
  overflow: hidden;
  width: 100%;
}

.messages-container {
  flex: 1;
  overflow-y: auto;
  padding: 20px 30px; /* Match the padding with header */
  width: calc(100% - 300px); /* Account for media preview width */
}

.media-preview {
  width: 300px;
  min-width: 300px; /* Prevent shrinking */
  padding: 15px;
  background-color: #ffffff;
  border-left: 1px solid #eaedf1;
  overflow-y: auto;
}

.media-section, .files-section {
  margin-bottom: 20px;
}

.media-section h4, .files-section h4 {
  margin-bottom: 15px;
  font-size: 16px;
  font-weight: 600;
}

/* Updated media grid with more columns for smaller images */
.media-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 8px;
}

/* Reduced size of media items with padding to maintain spacing */
.media-item {
  aspect-ratio: 1;
  border-radius: 6px;
  overflow: hidden;
  max-width: 80px;
  max-height: 80px;
  margin: 0 auto;
}

.media-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.files-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.message-input-container {
  padding: 15px 30px;
  background-color: white;
  border-top: 1px solid #eaedf1;
  border-right: 1px solid #eaedf1;

  width: calc(100% - 300px); /* Match width with messages container */
  box-sizing: border-box;
  margin-right: 300px; /* Account for media preview */
}

.message-input {
  display: flex;
  align-items: center;
  background-color: #f5f7fb;
  border-radius: 4px;
  padding: 8px 12px;
  width: 100%; /* Ensure input takes full width of container */
}

.emoji-btn {
  background: none;
  border: none;
  color: #6c757d;
  cursor: pointer;
  margin-right: 8px;
}

.message-input input {
  flex: 1;
  background: none;
  border: none;
  outline: none;
  font-size: 14px;
}
.input-actions {
  display: flex;
}

.attach-btn, .mic-btn {
  background: none;
  border: none;
  color: #6c757d;
  cursor: pointer;
  padding: 0 8px;
}
</style>