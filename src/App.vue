<template>
  <div id="app">
    <h1>2019's BEST BLOG POSTS</h1>
    <app-posts></app-posts>
    <footer>Copyright &copy; {{year}}</footer>
  </div>
</template>

<script>
import Posts from "./components/Posts.vue";

export default {
  name: "app",
  components: {
    appPosts: Posts
  },
  data: function() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Major+Mono+Display&display=swap");
html {
  border: 0;
  margin: 0;
  background-color: #f4faff;
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #595f72;
    margin-top: 60px;
    max-width: 1000px;
    margin: 0 auto;

    h1 {
      font-family: "Major Mono Display", monospace;
      text-align: center;
      font-size: 52px;
      color: #3b28cc;
      padding: 2% 10%;
      @media (max-width: 768px) {
        font-size: 32px;
      }
    }
    footer {
      text-align: center;
      margin-top: 20px;
    }
    .container {
      text-align: center;
      @media (max-width: 768px) {
        width: 100%;
        margin: 0 auto;
      }
      .card {
        display: block;
        position: relative;
        background-color: #9fffde;
        padding: 5px 15px;
        margin: 15px 20%;
        @media (max-width: 768px) {
          width: 80%;
          margin: 15px auto;
        }
        .x {
          text-align: right;
          position: absolute;
          right: 5px;
          cursor: pointer;
        }
        .username {
          color: #e56399;
        }
      }
      .card::before {
        content: "";
        position: absolute;
        width: 100%;
        height: 100%;
        top: -10px;
        right: -10px;
        border: 1px solid #e56399;
        z-index: -1;
      }
      .pag-button {
        background-color: inherit;
        border: none;
        border-bottom: 1px solid black;
        border-right: 1px solid black;
        padding: 5px 10px;
        margin: 5px;
      }
    }
  }
}
</style>
