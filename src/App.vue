<template>
  <div id="app">
    <navbar title='Hacker Jobs' />
    <jobs-list :jobs='jobs'></jobs-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import Navbar from './components/Navbar.vue'
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
      'navbar': Navbar,
      'jobs-list': JobsList
  }
}
</script>

<style>
html {
  text-size: 16px;
}

body {
  font-family: Verdana, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: black;
  color: white;
}
</style>
