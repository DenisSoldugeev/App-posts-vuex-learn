<template>
  <div id="app">
    <PostsForm />
    <h1>{{postsCount}}</h1>
      <div class="post" v-for="post in validPosts" :key="post.id">
        <h2>{{post.title}}</h2>
        <p>{{post.body}}</p>
      </div>
  </div>
</template>

<script>
import PostsForm from './components/PostForm'
import {mapGetters, mapActions} from 'vuex'

export default {
  name: 'App',
  computed: mapGetters(["validPosts", "postsCount"]),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts()
  },
  components: {
    PostsForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}
.post {
  border: 1px solid #cecece;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
