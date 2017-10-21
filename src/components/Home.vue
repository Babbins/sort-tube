<template>
  <div class="container">
    <Search @getData="getData"/>
    <VideoList :videos="videos" />
  </div>
</template>

<script>
import Search from './Search'
import VideoList from './VideoList'
import axios from 'axios'
import {apiKey} from '../secrets.json'
const apiURL = `https://www.googleapis.com/youtube/v3/search`

export default {
  name: 'Home',
  data: function () {
    return {
      videos: []
    }
  },
  methods: {

    getData (query) {
      const self = this
      axios.get(apiURL, {
        params: {
          q: query.term,
          key: apiKey,
          part: 'snippet',
          order: query.order,
          publishedAfter: query.uploadDate
        }
      })
      .then(function (response) {
        self.videos = response.data.items
        console.log(response)
      })
    }
  },
  components: { Search, VideoList }
}
</script>

<style scoped>
  header {
    position: fixed;
    width: 100%;
    top: 0;
    height: 55px;
    border-bottom: 2px red solid;
    text-align: center;
  }
  #logo {
    width: 30px;
    position: absolute;
    transform: translateY(50%);
    left: 10px;
  }
</style>
