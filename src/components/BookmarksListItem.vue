<template>
  <li><a v-bind:href="job.url">{{ job.title }}</a></li>

</template>

<script>
// import {eventBus} from '../main.js'
export default {
  props: ['job'],
}
</script>

<style lang="css" scoped>

li {
  list-style-type: none;
  color: white;
}

</style>