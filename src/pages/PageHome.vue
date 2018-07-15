<template>
  <div class="col-full">
    <h1>Welcome to the forum</h1>
    <ForumList :forums="forums"/>
  </div>
</template>

<script>
import sourdeData from '@/data'
import ForumList from '@/components/ForumList'
console.log(sourdeData)
export default {
  components: {
    ForumList
  },
  data () {
    return {
      forums: Object.values(sourdeData.forums),
      posts: sourdeData.posts,
      users: sourdeData.users
    }
  }
}
</script>
