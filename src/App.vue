<template>
  <Header />
  <Content />
  <h1 class="text-danger">Hy GUYS</h1>
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";
import Footer from "./components/Footer.vue";

export default {
  name          : "App",
  components    : {
    Header,
    Content,
    Footer
  }
};
</script>

<style>

  body{
    padding: 0;
    margin: 0;
  }

  .text-danger{
    color: blue;
  }
</style>