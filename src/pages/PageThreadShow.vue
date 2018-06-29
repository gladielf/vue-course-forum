<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :posts="posts"/>
    <form @submit.prevent="addPost">
      <div class="form-group">
        <textarea
        name=""
        id=""
        cols="30"
        rows="10"
        class="form-input"
        v-model="newPostText"
        ></textarea>
      </div>
      <div class="form-actions">
        <button class="btn-blue">Submit post</button>
      </div>
    </form>
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
        thread: sourdeData.threads[this.id],
        newPostText: ''
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
      addPost () {
        const postId = `greatPost${Math.random()}`
        const post = {
          text: this.newPostText,
          publishedAt: Math.floor(Date.now() / 1000),
          threadId: this.id,
          userId: 'VXjpr2WHa8Ux4Bnggym8QFLdv5C3',
          '.key': postId
        }
        this.$set(sourdeData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourdeData.users[post.userId].posts, postId, postId)
        this.newPostText = ''
      }
    }
  }
</script>
