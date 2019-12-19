<template id="posts">
  <div class="container">
    <h1>Users:</h1>
    <ul>
      <li v-for="person in people" :key="person.id" v-text="person.name"></li>
    </ul>
    <h1>Posts:</h1>
    <div class="card" v-for="post in posts" :key="post.id">
      <h4 v-text="post.title"></h4>
      <p v-text="post.body"></p>
      <div class="username" v-for="person in people" :key="person.id">
        <p v-if="post.userId === person.id" v-text="person.name"></p>
      </div>
    </div>\
  </div>
</template>

<script>
export default {
  props: ["people", "posts"],
  data: function() {
    return {
      users: this.people,
      postItems: this.posts
    };
  },
  methods: {}
};
</script>

<style lang="scss">
.container {
  background-color: aquamarine;
  text-align: center;
  width: 80%;
  margin: 0 auto;
  .card {
    border: 1px solid black;
    margin: 10px;
    .username {
      color: blueviolet;
    }
  }
}
</style>
