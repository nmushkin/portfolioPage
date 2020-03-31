var axios = require('axios');

<template>
  <div class="background">
    <div class="container">
      <div class="blog_body">
        <!-- <logo /> -->
        <h1 class="title-dark">
          {{ post.Title }}
        </h1>
        <img class="cover-image" :src="'http://localhost:1337' + post.cover" />
        <div class="blog_content" v-html="post.Entry_body"></div>
      </div>
    </div>
  </div>
</template>

<script>
import showdown from 'showdown'
const converter = new showdown.Converter()
export default {
  name: 'ProjectPost',
  data() {
    return {
      post: {}
    }
  },
  created() {
    this.loadPost()
  },
  methods: {
    loadPost() {
      this.$axios
        .get('http://localhost:1337/entries/' + this.$route.params.id)
        .then((response) => {
          this.post = response.data
          this.post.cover = response.data.entry_pics[0].url
          this.post.Entry_body = converter.makeHtml(this.post.Entry_body)
        })
      // this.post = post
    }
  }
}
</script>

<style scoped>
.container {
  margin: 0 auto;
  display: block;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.cover-image {
  width: 100%;
  max-width: 500px;
  object-fit: cover;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 4px;
}
.links {
  padding-top: 15px;
}
.blog_body {
  width: 80%;
  padding-bottom: 5vh;
}
.blog_content {
  text-align: left;
  max-width: 100%;
  overflow: hidden;
}
.blog_content >>> img {
  max-width: 100%;
  text-align: center;
}
</style>
