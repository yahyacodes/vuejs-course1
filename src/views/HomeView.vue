<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>Loading.....</div>
  </div>
</template>

<script>
import getPosts from "../composable/getPosts";
import PostList from "../components/PostList.vue";

export default {
  name: "HomeView",

  // Using Composition API
  // this keyword is not available in setup function
  // Values in setup function are not reactive by default
  // While values in data function are reactive y default
  // To make a value in setup functon reactive use ref

  setup() {
    const { posts, error, load } = getPosts();

    load();

    return {
      posts,
      error,
    };
  },
  components: {
    PostList,
  },
};
</script>
