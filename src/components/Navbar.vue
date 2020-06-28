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
  color: white;
  background-color: #121212;
  padding: 5px;
}
</style>