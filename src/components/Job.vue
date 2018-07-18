<template lang="html">
  <div>
    <h2>Jobs</h2>
    <jobitem v-for="story in stories" :key="story.data.id" :story="story"></jobitem>
  </div>
</template>

<script>
// import axios from 'axios'
import JobItem from '@/components/JobItem'
export default {
  name: 'Jobs',
  components: {
    'jobitem': JobItem
  },
  data: function () {
    return {
      err: '',
      stories: this.$store.state.jobStories
    }
  },
  created: function () {
    if(this.$store.state.jobStories.length === 0)
      this.$store.dispatch('fetch_job_stories')
  }
}
</script>

<style scoped>
</style>
