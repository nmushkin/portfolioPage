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
        <p>
          {{ post.Entry_body }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
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
</style>
