<template>
  <h1>{{ post.title }}</h1>
</template>

<script>
  import axios from 'axios'

  export default {
    async asyncData ({ params }) {
      const { data: post }  = await axios.get(`https://api.nuxtjs.dev/posts/${params.id}`)
      return { post }
    }
  }
</script>
