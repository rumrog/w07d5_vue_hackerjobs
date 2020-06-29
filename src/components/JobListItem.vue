<template>
  <li>
    <p>{{ job.title }}</p><a v-bind:href="job.url">({{ job.url }})</a>
    <br>
    <p class='time_ago'>{{ job.time_ago }}</p>
    <button v-on:click='addBookmark'>bookmark</button>
  </li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'job-list-item',
  props: ['job'],
  methods: {
    addBookmark: function() {
      eventBus.$emit('bookmark-added', this.job)
    }
  }
};
</script>

<style scoped>
li {
  list-style-type: none;
  color: white;
}
.time_ago {
  color: #d8d8d8;
}
</style>