<template>
  <div class="sidenav">

  </div>
</template>

<script>
export default {
  name: 'SideNav',
  components: {

  },
  mounted() {
    console.log('sidenav loaded');
  }
}
</script>

<style>
/*@import "https://cdn.rawgit.com/band-x-media/SASS-Material-Design-for-Bootstrap/master/dist/material-bootstrap.min.css";*/
/*
* Get some ideas from this bootstrap material design website
* http://code.band-x.media/SASS-Material-Design-for-Bootstrap/layout/navigation-drawer/
*/
.sidenav {
  position:fixed;
  top:52px;
  left:0;
  background-color:#333;
  width:300px;
  height:100%;
}
</style>
