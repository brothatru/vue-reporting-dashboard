<template>
  <div class="sidenav">
    <ul class="sidenav-ul">
      <a v-for="item in items" href="javascript:;">
        <!-- <li>{{item.title}}</li> -->
        <li>{{item.title}}</li>
      </a>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SideNav',
  components: {

  },
  data() {
    return {
      items: [
        { title: "Menu Item 1", link: "#" }
      ]
    }
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
@import url('https://fonts.googleapis.com/css?family=Roboto:400,400i,700');

.sidenav {
  position:fixed;
  top:52px;
  left:0;
  background-color:#333;
  width:300px;
  height:100%;
  color:#fff;
  font-family: 'Roboto', sans-serif;
  letter-spacing: 0.03em;
}
.sidenav-ul {
  border:1px red dashed;
  width:100%;
  height:100%;
  list-style:none;
  padding:0
}
.sidenav-ul a {
  display: block;
  color:#fff;
  font-size:16px;
}
hr.divider {

}
</style>
