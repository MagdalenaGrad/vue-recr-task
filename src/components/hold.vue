<template id="posts">
  <div class="container">
    <div class="card" v-for="(post, i) in posts" :key="i">
      <h4>{{ post.title }}</h4>
      <div @click="deletePost(post.id, i)">x</div>
      <p>
        {{ shrink(post.body) }}
        <span class="show">...</span>
      </p>
      <div class="username" v-for="user in users" :key="user.id">
        <p v-if="post.userId === user.id">{{ user.name }}</p>
      </div>
    </div>
    <button type="button">prev</button>
    <button type="button">1</button>
    <button type="button">next</button>
  </div>
</template>

<script>
import axios from "axios";
window.axios = require("axios");

export default {
  data: function() {
    return {
      posts: [],
      users: [],
      page: 1,
      perPage: 10,
      pages: []
    };
  },
  props: {},
  methods: {
    getPosts: function() {
      axios.get("https://jsonplaceholder.typicode.com/posts").then(res => {
        this.posts = res.data;
        console.log(this.posts);
      });
    },
    getUsers: function() {
      axios.get("https://jsonplaceholder.typicode.com/users").then(res => {
        res.data.forEach(x => {
          console.log(x.name);
        });
        this.users = res.data;
      });
    },
    deletePost: function(item, index) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${item.id}`)
        .then(res => {
          this.posts.splice(index, 1);
          console.log(res, this.posts);
        });
    },
    shrink: function(str) {
      return str.substring(0, 80);
    }
  },
  created: function() {
    this.getUsers();
    this.getPosts();
  },
  mounted: function() {}
};
</script>

<style lang="scss">
.container {
  background-color: aquamarine;
  text-align: center;
  width: 80%;
  margin: 0 auto;
  .show {
    cursor: pointer;
    border: 1px solid black;
  }
  .card {
    border: 1px solid black;
    margin: 10px;
    .username {
      color: blueviolet;
    }
  }
}
</style>

