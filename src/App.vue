<template>
  <div class="container">
    <table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr v-if="loading">
      Loading...
    </tr>
    <tr v-else v-for="(post, index) in posts" :key="post.id">
      <th scope="col">{{index+1}}</th>
      <th scope="col">{{post.title}}</th>
      <th scope="col">{{post.content}}</th>
      <th scope="col">{{post.image}}</th>
    </tr>
  </tbody>
</table>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import axios from "axios";

export default {
  name          : "App",
  components    : {},
  setup(){  
    const posts     = ref([]);
    const loading   = ref([]);
    const error     = ref("");
    
    onMounted(async ()  =>{
      try {
        loading.value   = true
        const response  = await axios.get("http://127.0.0.1:8000/api/post")

        posts.value     = response.data.data;
        loading.value   = false
      } catch (err) {
        error.value     = "Internet Tidak Terhubung"
        loading.value   = false
      }
     
    })

    return {
      posts,
      loading,
      error
    }
  }
};
</script>

<style>

  body{
    padding: 0;
    margin: 0;
  }

</style>