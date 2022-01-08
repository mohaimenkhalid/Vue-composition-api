<template>
  <div>
    <div v-for="post in posts" :key="post.title">
      <div>
        <SinglePost :post="post" />
      </div>
      <hr />
    </div>
  </div>
</template>

<script>
  import SinglePost from "@/components/SinglePost";
  export default {
    name: "PostList",
    components: {SinglePost},
    props: ['posts'],
    setup(props) {

    }
  }
</script>
