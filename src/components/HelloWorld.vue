<template>
  <div>
    <h1>Axios</h1>

    <div>
      <el-row :gutter="40">
        <el-col class="column" v-for="post in posts"  :span="10"><div class="grid-content bg-purple-dark">
      <el-card :key="post.id">
        <div slot="header">
          <h3>Title: {{ post.title }}</h3>
      </div>
      <p class="body">Description: {{ post.body }}</p>
      <p><a v-bind:href="postsLink">Posts</a></p>
      <p><a v-bind:href="commentsLink">Comments</a></p>
      </el-card>
      </div>
    </el-col>
    </el-row>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      posts: [],
      postsLink: 'https://jsonplaceholder.typicode.com/posts',
      commentsLink: 'https://jsonplaceholder.typicode.com/comments'
    }
  },
  mounted() {
    var self = this;
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then( function(res){
        self.posts = res.data;
        console.log('Data: ',res.data);
      })
      .catch( function(error){
        console.log('Error: ',error);
      })
  }
}
</script>

<style scoped>

.column:nth-child(odd) {
  clear: both;
}

.column {
  margin:15px;
}

  .post {
    background: #ccc;
    margin-bottom: 20px;
    padding: 10px 20px;
  }
  h3 {
    text-align: left;
  }
  p {
    text-align: left;
    margin: 15px;
    padding: 10px;
  }
</style>
