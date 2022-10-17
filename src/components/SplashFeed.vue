<template>
  <div class="feed">
    <div class="scroll-feed" v-if="photosArray" >
      <FeedCard v-for="photo in photosArray" :key="photo.id"  :photo=photo></FeedCard>
    </div>
    <div class="item-view" v-if="selectdPhoto"></div>
    <div class="item-view" v-else>
      <img src="../assets/empty.svg" />
      <h3>No Photo Selected</h3>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import FeedCard from './FeedCard.vue'
export default {
  name: 'SplashFeed',
  components: {
    FeedCard
  },
  data : () => ({
    photosArray:null,
    selectdPhoto:null
  }),
  mounted: function(){
    this.getPhotos()
  },
  methods :{
    async getPhotos(){
      const res = await axios.get(`https://api.unsplash.com/photos/?client_id=q7_-eEbuDJXNJo1hqmJqkM81oyibAv0rCLoha0SAtHk`)
      console.log(res.data)
      this.photosArray = res.data
    }
  }
}
</script>

<style>
.feed {
  display: flex;
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
