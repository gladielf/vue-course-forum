<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :posts="posts"/>
    <PostEditor
      :threadId="id"
      @save="addPost"/>

  </div>
</template>

<script>
  import sourdeData from '@/data'
  import PostList from '@/components/PostList'
  import PostEditor from '@/components/PostEditor'
  export default {
    components: {
      PostList,
      PostEditor
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
    },
    methods: {
      addPost (eventData) {
        const post = eventData.post
        const postId = eventData.post['.key']

        this.$set(sourdeData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourdeData.users[post.userId].posts, postId, postId)
      }
    }
  }
</script>
