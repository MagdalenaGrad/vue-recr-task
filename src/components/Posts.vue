<template>
  <div>
    <h1>Users:</h1>
    <ul>
      <li v-for="user in users" :key="user.id" v-text="user.name"></li>
    </ul>
    <h1>Posts:</h1>
    <ul>
      <li v-for="post in posts" :key="post.id" v-text="post.body"></li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
window.axios = require("axios");

export default {
  methods: {
    getPosts: async function() {
      await axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then(res => {
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
  },
  data: function() {
    return {
      posts: null,
      users: null
    };
  }
};
</script>

<style>
</style>