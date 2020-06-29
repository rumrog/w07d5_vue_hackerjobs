<template>
  <div class='job-list'>
    <ul>
      <job-list-item 
      v-for="(job, index) in jobs" 
      :job="job" 
      :key="index">
      </job-list-item>
    </ul>
  </div>
</template>

<script>
import JobListItem from './JobListItem'

export default {
  name: 'job-list',
  props: ['jobs'],
  components: {
    'job-list-item': JobListItem
  }  
}
</script>

<style lang="css" scoped>
  .job-list {
    height: 500px;
    overflow-y: scroll;
  }
</style>