<template>
  <div class="container">
    <h1 class="text-primary">Helo World</h1>
    <!-- <button class="btn btn-primary" @click="heloworld()">
      Click saya
    </button> -->
    <div v-if="show">
      <div class="row" >
        <Card 
        v-for="post in posts" 
        :key="post.id" 
        :post="post"
        title="sasasa"
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
</template>

<script>
import { ref } from "vue";
import Card from "./components/Card.vue";
export default {
  name          : "App",
  components    : {Card},
  setup(){
    const show  = ref(true);

    const posts = [
      {
        id : 1,
        name : "belajar laravel"
      },
      {
        id : 2,
        name : "belajar vue"
      },
      {
        id : 3,
        name : "belajar livewire"
      },
    ];

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
      toggleChange 
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