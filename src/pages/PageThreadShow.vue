<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <p>
      By <a href="#" class="link-unstyled">Robin</a>, <app-date :timestamp="thread.publishedAt"/>.
      <span style="float:right; margin-top: 2px;" class="hide-mobile text-faded text-small">3 replies by 3 contributors</span>
    </p>
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
      addPost ({post}) {
        const postId = post['.key']

        this.$set(sourdeData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourdeData.users[post.userId].posts, postId, postId)
      }
    }
  }
</script>
