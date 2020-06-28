<template>
  <div id="app">
    <h1>Hacker Jobs</h1>
    <jobs-list :jobs='jobs'></jobs-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import ListComponent from './components/ListComponent.vue'
import JobsList from './components/JobsList.vue'

export default {
  name: 'App',
  data() {
    return {
      jobs: [],
      selectedJob: null
    }
  },
    mounted() {
      fetch("https://api.hackerwebapp.com/jobs?page=1")
      .then(res => res.json())
      .then(jobs => this.jobs = jobs)

      eventBus.$on('job-selected', (job) => {
        console.log(job.title);

        this.selectedJob = job
      })
    },
    components: {
    "jobs-list": JobsList
  }
}
</script>

<style>
body {
  font-family: Verdana, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #121212;
  color: white;
}
</style>
