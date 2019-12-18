<template>
  <div id="app">
    <app-posts></app-posts>
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
