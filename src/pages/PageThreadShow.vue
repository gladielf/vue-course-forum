<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :posts="posts"/>
  </div>
</template>

<script>
  import sourdeData from '@/data'
  import PostList from '@/components/PostList'
  export default {
    components: {
      PostList
    },
    props: {
      id: {
        required: true,
        type: String
      }
    },
    data () {
      return {
        thread: sourdeData.threads[this.id]
      }
    },
    computed: {
      posts () {
        const postsId = Object.values(this.thread.posts)
        return Object.values(sourdeData.posts)
          .filter(post => postsId.includes(post['.key']))
      }
    }
  }
</script>
