<template>
  <header>
    {{ getData() }}
  </header>
</template>

<script>
import axios from 'axios'
import {apiKey} from '../secrets.json'

var apiURL = `https://www.googleapis.com/youtube/v3/search`

export default {
  name: 'Home',
  data: function () {
    return {
      videos: []
    }
  },
  methods: {
    getData: function () {
      axios.get(apiURL, {
        params: {
          key: apiKey,
          part: 'snippet',
          order: 'viewCount',
          publishedAfter: '2017-10-15T20:19:55.413Z'
        }
      })
      .then(function (response) {
        console.log(response)
      })
    }
  }
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
