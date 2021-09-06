<template>
  <div id="app">
    <Header/>
    <Container/>
    <Footer/>
  </div>
</template>

<script>

import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Container from './components/Container.vue';

export default {
  name: 'App',
  components: {
    Header,
    Container,
    Footer
  }
}
</script>

<style>
html, body{
  margin: 0;
  padding: 0;
}
</style>
