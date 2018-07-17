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
  name: 'Homepage',
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
    if (this.$store.state.newStories.length === 0)
      this.$store.dispatch('fetch_new_stories')
    // https://hacker-news.firebaseio.com/v0/topstories.json
    // axios.get('https://hacker-news.firebaseio.com/v0/newstories.json')
    //   .then((response)=> {
    //     let results = response.data.slice(0,25)
    //     results.forEach(id => {
    //       axios.get('https://hacker-news.firebaseio.com/v0/item/' + id + '.json')
    //         .then((response) => {
    //           this.stories.push(response)
    //         })
    //         .catch((err) => {
    //           this.err = err
    //         })
    //     })
    //   })
    //   .catch((err)=> {
    //     this.err = err
    //   })
  }
}
</script>

<style scoped>
</style>
