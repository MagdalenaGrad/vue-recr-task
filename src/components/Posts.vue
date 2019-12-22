<template id="posts">
  <div class="container">
    <div class="card" v-for="(post, i) in displayedPosts" :key="i">
      <div class="x" @click="deletePost(post.id, i)">x</div>
      <h4>{{ post.title }}</h4>
      <app-post-body :pbody="post.body"></app-post-body>
      <div class="username" v-for="user in users" :key="user.id + 'l'">
        <p v-if="post.userId === user.id">{{ user.name }}</p>
      </div>
    </div>
    <!-- pagination buttons -->
    <div class="pagination">
      <button class="pag-button" type="button" v-if="page != 1" @click="page--">prev</button>
      <button
        class="pag-button"
        type="button"
        v-for="(pageNumber, i) in pages.slice(page - 1, page + 5)"
        v-bind:key="i + 'm'"
        @click="page=pageNumber"
      >{{ pageNumber }}</button>
      <button class="pag-button" type="button" @click="page++" v-if="page < pages.length">next</button>
    </div>
  </div>
</template>

<script>
import PostBody from "./PostBody.vue";
import axios from "axios";
window.axios = require("axios");

export default {
  components: {
    appPostBody: PostBody
  },
  data: function() {
    return {
      posts: [],
      users: [],
      page: 1,
      perPage: 10,
      pages: []
    };
  },
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
    // pagination methods:

    paginate: function(posts) {
      let page = this.page;
      let perPage = this.perPage;
      let from = page * perPage - perPage;
      let to = page * perPage;
      return posts.slice(from, to);
    },
    setPages: function() {
      let numberOfPages = Math.ceil(this.posts.length / this.perPage);
      for (let i = 1; i <= numberOfPages; i++) {
        this.pages.push(i);
      }
    }
  },
  created: function() {
    this.getUsers();
    this.getPosts();
  },
  watch: {
    posts() {
      this.setPages();
    }
  },
  computed: {
    displayedPosts() {
      return this.paginate(this.posts);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>

