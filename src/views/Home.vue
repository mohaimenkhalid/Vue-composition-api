<template>
  <h1>Post List</h1>
  <div v-if="error">{{error}}</div>
  <PostList :posts="posts" />
</template>

<script>
import {ref, reactive, computed, watch, watchEffect} from 'vue'
import PostList from "@/components/PostList";
export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const posts = ref([]);
    const error = ref(null);

    const load = async () => {
      try {
        let data = await fetch('http://localhost:3000/posts')
        if (!data.ok) {
          throw Error('No data available.')
        }
        posts.value = await data.json();

      } catch (err) {
        error.value = err.message
        console.log(err.message)
        console.log(err.value)
      }
    }
    load()


    return {
      posts,
      error
    }
  }
}
</script>
