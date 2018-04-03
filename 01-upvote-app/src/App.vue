<template>
  <div id="app">
    <h1 class="title is-1 has-text-centered dividing-header">Upvote!</h1>
    <Posts/>
  </div>
</template>

<script>
import Posts from './components/Posts'

export default {
  name: 'App',
  components: {
    Posts
  }
}
</script>