<template>
  <li v-on:click='handleClick'>
    <p>{{ job.title }}</p><a v-bind:href="job.url">({{ job.url }})</a>
    <br>
    <p>{{ job.time_ago }}</p>
  </li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-component',
  props: ['job'],
  methods: {
    handleClick(){
      eventBus.$emit('job-selected', this.job)
    }
  }
};
</script>

<style scoped>
li {
  list-style-type: none;
}
</style>