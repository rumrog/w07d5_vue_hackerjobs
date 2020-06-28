<template>
  <li v-on:click='handleClick'><h2>{{ job.title }}</h2></li>
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