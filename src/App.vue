<template>
  <div class="container">
    <h1 class="text-primary">Helo World</h1>
    <!-- <button class="btn btn-primary" @click="heloworld()">
      Click saya
    </button> -->
    <div v-if="error">error : {{error}}</div>
    <div v-if="loading">
      Loading...
    </div>
    <div v-if="!loading">
      <div v-if="show">
        <div class="row" >
          <Card 
          v-for="post in posts" 
          :key="post.id" 
          :post="post"  
          />
        </div>
      </div>
      <div v-else>
        Mantap Datanya Kosong
      </div>    
      <button class="btn btn-danger" @click="toggleChange()">
        Show/Hide
      </button>
    </div>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import Card from "./components/Card.vue";
import axios from "axios";

export default {
  name          : "App",
  components    : {Card},
  setup(){
    const show      = ref(true);
    const posts     = ref([]);
    const loading   = ref([]);
    const error     = ref("");
    
    onMounted(async ()  =>{
      try {
        loading.value   = true
        const response  = await axios.get("https://jsonplaceholder.typicode.com/posts")

        posts.value     = response.data;
        loading.value   = false
      } catch (err) {
        error.value     = "Internet Tidak Terhubung"
        loading.value   = false
      }
     
    })

    const heloworld = () => {
      alert("MONZA NI BOS!!")
    };

    const toggleChange= () =>{
      show.value = !show.value;
    }

    return {
      heloworld,
      posts,
      show,
      toggleChange ,
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