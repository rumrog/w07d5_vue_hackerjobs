<template>
  <li><a v-bind:href="job.url">{{ job.title }}</a></li>

</template>

<script>
export default {
  props: ['job'],
}
</script>

<style lang="css" scoped>


</style>