<template>
  <div class="thread">
    <div>
      <p> <a href="#">{{thread.title}}</a> </p>
      <p class="text-faded text-xsmall">
        By <a href="">{{user.name}}</a>, {{thread.publishedAt}}.
      </p>
    </div>

    <div class="activity">
      <p class="replies-count">
        {{repliesCount}} replies
      </p>

      <!-- <img src="" alt="" class="avatar-medium"> -->

      <!-- <div>
        <p class="text-xsmall">
          <a href="">Bruce Wayne</a>
        </p>
        <p class="text-xsmall text-faded">2 hours ago</p>
      </div> -->

    </div>

  </div>
</template>

<script>
  import sourdeData from '@/data'
  export default {
    props: {
      thread: {
        required: true,
        type: Object
      }
    },
    computed: {
      repliesCount () {
        return Object.keys(this.thread.posts).length - 1
      },
      user () {
        return sourdeData.users[this.thread.userId]
      }
    }
  }
</script>
