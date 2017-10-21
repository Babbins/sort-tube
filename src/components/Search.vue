<template>
  <div class="search">
    <input v-model="term" type="text" placeholder="Puppies!" @keyup.enter="submit">
    <select v-model="uploadDate">
      <option value="hour">Last Hour</option>
      <option value="day">Today</option>
      <option value="week">This week</option>
      <option value="month">This month</option>
      <option value="year">This year</option>
    </select>
    <select v-model="sortBy">
      <option value="relevance">Relevance</option>
      <option value="uploadDate">Upload date</option>
      <option value="viewCount">View Count</option>
      <option value="rating">Rating</option>
    </select>
    <button type="button" @click="submit">Search</button>
  </div>
</template>

<script>
// import timeUtils from ../utils/time.js
import moment from 'moment'
export default {
  name: 'Search',
  data: function () {
    return {
      term: '',
      uploadDate: 'day',
      sortBy: 'viewCount'
    }
  },
  methods: {
    submit () {
      this.$emit('getData', {
        term: this.term,
        uploadDate: moment().subtract(1, this.uploadDate).toDate().toISOString(),
        order: this.sortBy
      })
    }
  }
}
</script>

<style scoped>

</style>
