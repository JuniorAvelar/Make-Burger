<template>
  <div>
    <Banner/>
    <div class="main-container">
    <h1>Monte o seu Burger:</h1>
    <p>Formuladrio</p>
  </div>
  </div>
</template>

<script>
 import Banner from '@/components/Banner.vue';

  export default {
    name: 'HomeView',
    components: {
      Banner,
    }
  }

</script>
