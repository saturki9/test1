<template>
  <div class="file-item">
    <div class="file-icon">
      <img :src="getIconSrc()" alt="file icon" class="icon-image" />
    </div>
    <div class="file-info">
      <div class="file-name">{{ file.name }}</div>
      <div class="file-details">{{ file.size }} · {{ file.date }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FileItem',
  props: {
    file: {
      type: Object,
      required: true
    }
  },
  methods: {
    getIconSrc() {
      const iconMap = {
        'pdf': require('@/assets/icons/pdf-icon.png'),
        'fig': require('@/assets/icons/fig-icon.png'),
        'html': require('@/assets/icons/html-icon.png'),
        'zip': require('@/assets/icons/zip-icon.png'),
        'js': require('@/assets/icons/js-icon.png')
      };
      return iconMap[this.file.icon] || require('@/assets/icons/default-icon.png');
    }
  }
}
</script>

<style scoped>
.file-item {
  display: flex;
  align-items: center;
  padding: 8px 0;
}

.file-icon {
  width: 35px;
  height: 35px;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 12px;
}

.icon-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.file-info {
  flex: 1;
}

.file-name {
  font-size: 14px;
  font-weight: 500;
}

.file-details {
  font-size: 12px;
  color: #6c757d;
}
</style>
