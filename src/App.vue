<template>
  <div id="app">
    <app-posts :people="users" :posts="posts"></app-posts>
  </div>
</template>

<script>
import Posts from "./components/Posts.vue";
import axios from "axios";
window.axios = require("axios");

export default {
  name: "app",
  components: {
    appPosts: Posts
  },
  data: function() {
    return {
      posts: null,
      users: null
    };
  },
  props: {},
  methods: {
    getPosts: function() {
      axios.get("https://jsonplaceholder.typicode.com/posts").then(res => {
        console.log(res);
        this.posts = res.data;
      });
    },
    getUsers: function() {
      axios.get("https://jsonplaceholder.typicode.com/users").then(res => {
        console.log(res);
        this.users = res.data;
      });
    }
  },
  mounted: function() {
    this.getUsers();
    this.getPosts();
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
