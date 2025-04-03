<template>
<div>
  <Navbar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer/>
</div>
</template>

<script>
  import Footer from './components/Footer.vue';
  import Navbar from './components/Navbar.vue';

  export default {
    components: {
      Navbar,
      Footer
    },
    data() {
      return {
        logo_src: '/img/logo.png',
        app_name: 'make Burguer'
      }
    }
   
  }
</script>

<style>
  * {
    font-family: helvetica;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html, body {
  margin: 0;
  padding: 0;
  height: 100%  ;
}

  .main-container {
    margin: 50px;
    min-height: 250px;
  }


  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color:#222
  }
</style>
