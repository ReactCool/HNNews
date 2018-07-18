<template lang="html">
  <div>
    <h2>Best Stories</h2>
    <item v-for="story in stories" :key="story.data.id" :story="story"></item>
  </div>
</template>

<script>
// import axios from 'axios'
import Item from '@/components/Item'
export default {
  name: 'Best',
  components: {
    'item': Item
  },
  data: function () {
    return {
      err: '',
      stories: this.$store.state.bestStories
    }
  },
  created: function () {
    if (this.$store.state.bestStories.length === 0)
      this.$store.dispatch('fetch_best_stories')
  }
}
</script>

<style scoped>
</style>
