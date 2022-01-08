<template>
  <h1>Post List</h1>
  <div v-if="error">{{error}}</div>
  <div v-if="posts.length">
    <PostList :posts="posts" />
  </div>
  <div v-else>
    Loading...
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import getPosts from "@/composables/getPosts";
export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const {load, error, posts} = getPosts();
    load()
    return {
      posts,
      error
    }
  }
}
</script>
