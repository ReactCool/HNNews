<template lang="html">
  <div>
    <h2>New Stories</h2>
    <item v-for="story in stories" :key="story.data.id" :story="story"></item>
  </div>
</template>

<script>
// import axios from 'axios'
import Item from '@/components/Item'
export default {
  name: 'New',
  components: {
    'item': Item
  },
  data: function () {
    return {
      err: '',
      stories: this.$store.state.newStories
    }
  },
  created: function () {
    if(this.$store.state.newStories.length === 0){
      this.$store.dispatch('fetch_new_stories')
    }
  }
}
</script>

<style scoped>
</style>
