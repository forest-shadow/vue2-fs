<template>
  <section class="posts">
    <div class="section">
      <Post v-for="post in sortedPosts" :key="post.id" :post="post" @upvote="upvote($event)"/>
    </div>
  </section>
</template>

<script>
import Post from './Post.vue';

import posts from '../posts.js';

export default {
  name: 'Posts',
  components: { Post },
  data() {
    return {
      posts: posts
    }
  },
  methods: {
    upvote(postId) {
      const post = this.posts.find(
        post => post.id === postId
      );
      post.votes++;
    }
  },
  computed: {
    sortedPosts () {
      return this.posts.sort((a, b) => {
        return b.votes - a.votes
      });
    }
  }
}
</script>

<style scoped>
</style>
