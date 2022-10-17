<template>
  <div class="item-view-content">
    <div class="stats row">
      <div class="user-info row">
        <img :src="photo.user.profile_image.small" />
        <h3>{{ photo.user.username }}</h3>
      </div>
      <div>
        <h4>{{ photo.downloads }} <span class="icon">&#10515;</span></h4>
        <h4>{{ photo.likes }} <span class="icon">&#9829;</span></h4>
      </div>
    </div>
    <div class="photo-container">
      <img :src="photo.urls.regular" />
    </div>
    <div class="badge row">
      <span :key="tag.title" v-for="tag in photo.tags">
        {{ tag.title }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailView',
  props: {
    photo: {}
  }
}
</script>

<style scoped>
.item-view-content {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.user-info img {
  border-radius: 50%;
}

.user-info h3 {
  margin-left: 1em;
}

.item-view-content img {
  max-height: 800px;
  margin: auto;
}

.photo-container {
  margin: auto;
  padding: 1em;
}

.stats {
  justify-content: space-between;
  width: 80%;
  margin: auto;
  border-bottom: 1px solid rgba(0, 0, 0, 0.3);
}

.row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.badge {
  width: 80%;
  margin: auto;
  align-items: flex-start !important;
  justify-content: flex-start;
}

.badge span {
  background-color: rgba(0, 191, 166, 0.3);
  margin: 0.5em;
  padding: 0.4em 0.6em;
  border-radius: 8px;
}

.icon {
  font-size: 1.4rem;
}
</style>
