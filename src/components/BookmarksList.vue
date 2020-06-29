<template>
  <div id='bookmarks-list'>
    <navbar title='Bookmarks'></navbar>
    <ul>
      <bookmarks-list-item
        v-for='(job, index) in bookmarks'
        :job='job'
        :key='index'>
      </bookmarks-list-item>
    </ul>
  </div>
</template>

<script>
import BookmarksListItem from './BookmarksListItem.vue'
import Navbar from './Navbar.vue'

export default {
  props: ['bookmarks'],
  components: {
    'bookmarks-list-item': BookmarksListItem,
    'navbar': Navbar
  }
}
</script>

<style lang="css" scoped>
ul {
  padding-bottom: 30px;
}
</style>