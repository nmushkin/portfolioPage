<template>
  <div class="container">
    <div>
      <!-- <logo /> -->
    </div>
    <BlogList />
  </div>
</template>

<script>
import BlogList from '~/components/BlogList'

export default {
  components: {
    BlogList
  }
}
</script>

<style scoped>
.container {
  margin: 0 auto;
  display: block;
  justify-content: center;
  align-items: center;
  text-align: center;
  /* background-color: #aaaaaa; */
}
.links {
  padding-top: 15px;
}
</style>
