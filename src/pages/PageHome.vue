<template>
  <div class="col-full">
    <h1>Welcome to the forum</h1>
    <ThreadList :threads="threads"/>
  </div>
</template>

<script>
import sourdeData from '@/data'
import ThreadList from '@/components/ThreadList'
console.log(sourdeData)
export default {
  components: {
    ThreadList
  },
  data () {
    return {
      threads: Object.values(sourdeData.threads),
      posts: sourdeData.posts,
      users: sourdeData.users
    }
  }
}
</script>
