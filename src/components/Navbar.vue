<template>
  <h2>{{ title }}</h2>
</template>

<script>
export default {
  name: 'navbar',
  props: ['title']
}
</script>

<style scoped>
h2 {
  font: bold 2em Verdana;
  color: #ECEFF4;
  background-color: #3B4252;
  padding: 5px;
}
</style>