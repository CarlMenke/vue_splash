<template>
  <div class="feed">
    <div>
      <div class="scroll-feed" v-if="photosArray" >
        <FeedCard v-for="photo in photosArray" :key="photo.id"  :photo=photo @selectPhoto="selectPhoto"/>
      </div>
    </div>
    <div>
      <div class="item-view" v-if="selectedPhoto">
        <DetailView :photo="selectedPhoto"/>
      </div>
      <div class="item-view" v-else>
        <img src="../assets/empty.svg" />
        <h3>No Photo Selected</h3>
      </div>
  </div>
  </div>
</template>

<script>
import axios from 'axios'
import DetailView from './DetailView.vue'
import FeedCard from './FeedCard.vue'
export default {
  name: 'SplashFeed',
  components: {
    FeedCard,
    DetailView
  },
  data : () => ({
    photosArray:null,
    selectedPhoto:null
  }),
  mounted: function(){
    this.getPhotos()
  },
  methods :{
    async getPhotos(){
      const res = await axios.get(`https://api.unsplash.com/photos/?client_id=q7_-eEbuDJXNJo1hqmJqkM81oyibAv0rCLoha0SAtHk`)
      console.log(res.data)
      this.photosArray = res.data
    },
    async selectPhoto(photoId) {
      const res = await axios.get(`https://api.unsplash.com/photos/${photoId}?client_id=q7_-eEbuDJXNJo1hqmJqkM81oyibAv0rCLoha0SAtHk`)
      console.log(res.data)
      this.selectedPhoto = res.data
    }
  }
}
</script>

<style>
.feed {
  display:flex;
  flex-flow:row nowrap;
}

.scroll-feed {
  flex: 1;
  overflow-y: scroll;
  height: 100vh;
}

.item-view {
  padding: 1em;
  align-items: center;
  justify-content: center;
  height: 50vh;
  width: 50vw;
}
</style>
