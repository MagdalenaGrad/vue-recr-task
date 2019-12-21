<template>
  <div id="app">
    <h1>Posts:</h1>
    <app-posts></app-posts>
    <!-- propsy do komponentu: :people="users" :posts="posts" -->
    <!-- <p>{{ shrink() }}</p> -->
  </div>
</template>

<script>
import Posts from "./components/Posts.vue";

export default {
  name: "app",
  components: {
    appPosts: Posts
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
