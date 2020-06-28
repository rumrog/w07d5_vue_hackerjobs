<template>
  <div>
    <ul>
      <list-component v-for="(job, index) in jobs" :job="job" :key="index"></list-component>
    </ul>
  </div>
</template>

<script>
import ListComponent from './ListComponent.vue'

export default {
  name: 'jobs-list',
  props: ['jobs'],
  components: {
    'list-component': ListComponent
  }  
}
</script>