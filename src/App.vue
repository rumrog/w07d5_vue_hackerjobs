<template>
  <div id="app">
    <navbar title='Hacker Jobs' />
    <job-list :jobs='jobs'></job-list>
    <bookmarks-list :bookmarks='bookmarks'></bookmarks-list>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import Navbar from './components/Navbar.vue'
import JobListItem from './components/JobListItem.vue'
import JobList from './components/JobList.vue'
import BookmarksList from './components/BookmarksList.vue'

export default {
  name: 'App',
  data() {
    return {
      jobs: [],
      selectedJob: null
    }
  },
  computed: {
    bookmarks: function() {
      return this.jobs.filter(job => job.isBookmark);
    }
  },
  methods: {
    getJobs: function() {
      fetch("https://api.hackerwebapp.com/jobs?page=1")
      .then(res => res.json())
      .then(jobs => {
        jobs.forEach(job => (job.isBookmark = false))
        this.jobs = jobs
      });
    },
    markBookmark: function(job) {
      const index = this.jobs.indexOf(job)
      this.jobs[index].isBookmark = true
    }

    // eventBus.$on('job-selected', (job) => {
    //   console.log(job.title);

    //   this.selectedJob = job
    // })
    
  },
  mounted() {
    this.getJobs()

    eventBus.$on('bookmark-added', job => this.markBookmark(job))
  },
  components: {
    'navbar': Navbar,
    'job-list': JobList,
    'bookmarks-list': BookmarksList
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
  background-color:#2E3440;
}

a {
  color: #D8D8D8;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
#app {
  background-color: #434C5E;
}
</style>
