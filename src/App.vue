<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <header-toolbar></header-toolbar>
    <side-nav></side-nav>
    <router-view></router-view>
  </div>
</template>

<script>
import HeaderToolbar from '@/components/HeaderToolbar';
import SideNav from '@/components/SideNav';
export default {
  name: 'app',
  components: {
    HeaderToolbar,
    SideNav
  }
}
</script>

<style>
body {
  margin:0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
</style>
