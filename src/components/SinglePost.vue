<template>
  <div>
    <h4>{{ post.title }}</h4>
    <p>{{ snippet }}</p>
  </div>
</template>

<script>
import {ref, reactive, computed, watch, watchEffect} from 'vue'
export default {
  name: "SinglePost",
  props: ['post'],
  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substring(0, 100) + '....'
    })
    return {
      snippet
    }
  }
}
</script>

<style scoped>

</style>
