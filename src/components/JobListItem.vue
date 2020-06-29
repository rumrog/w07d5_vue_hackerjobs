<template>
  <li>
    <div class='in-line'>
      <li><a class='title' v-bind:href="job.url">{{ job.title }}</a></li><a class='domain' v-bind:href="job.domain">({{ job.domain }})</a>
    </div>
    <div class='in-line'>
      <p class='time_ago'>{{ job.time_ago }}</p>
      <button style='font-size: 1em' v-on:click='addBookmark'>bookmark</button>
    </div>
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

.title {
  color: white;
}

.domain,
.time_ago {
  color: #A1A7B1;
  padding-right: 0.5em;
}

button {
  background: none !important;
  border: none;
  padding: 0 !important;
  margin: 0 !important;
  color: #81A1C1;
  cursor: pointer;
}

button:hover {
  text-decoration: underline;
}

button:focus {
  outline: none;
}

.in-line {
  display: flex;
}
</style>