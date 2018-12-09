<template>
  <div id="app">
    <the-navbar/>
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>

<script>
  import TheNavbar from '@/components/TheNavbar'
  export default {
    name: 'app',
    components: {
      TheNavbar
    }
  }
</script>

<style>
  @import "assets/css/styles.css";
</style>
