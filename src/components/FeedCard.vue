<template>
  <div class="card" @click="selectPhoto(photo.id)">
    <div class="card-header">
      <div class="info">
        <img :src="photo.user.profile_image.small" />
        <h3>{{ photo.user.username }}</h3>
      </div>
      <h4><span class="icon">&#9829; </span>{{ photo.likes }}</h4>
    </div>
    <div class="card-content">
      <div>
        <img :src="photo.urls.small" />
      </div>
      <div>
        <p>{{ photo.description }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'FeedCard',
  props: {
    photo: {}
  },
  methods: {
    selectPhoto(photoId) {
      console.log('here')
      this.$emit('selectPhoto', photoId)
    }
  }
}
</script>

<style scoped>
.card {
  border: 1px solid;
  border-radius: 8px;
  max-width: 400px;
  margin: 1em auto;
  cursor: pointer;
  transition: all 0.2s ease;
}

.card:hover {
  opacity: 0.7;
}
.icon {
  font-size: 1.3rem;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1em 0.5em;
}

.info {
  display: flex;
  align-items: center;
}

.card-header h3 {
  margin-left: 0.5em;
}

.card-header img {
  border-radius: 50%;
}

.card-content {
  text-align: center;
}
</style>
