<template>
  <div class="sidenav">
    <ul class="sidenav-ul">
      <a v-for="item in items" href="javascript:;">
      <!-- <a v-for="item in items"> -->
        <!-- <li>{{item.title}}</li> -->
        <li>
          <!-- <div>
            <i class="fa" :class="item.icon" aria-hidden="true"></i>
          </div>
          <div>
            <span>{{item.title}}</span>
          </div>
          <div>
            <i class="fa fa-angle-down" aria-hidden="true"></i>
          </div> -->
          <i class="fa" :class="item.icon" aria-hidden="true"></i> <span>{{item.title}}</span> <i class="fa fa-angle-down" aria-hidden="true"></i>
          <ul class="sidenav-sub-menu-ul">
            <a
          </ul>
        </li>
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
        { title: "Menu Item 1", icon: "fa-pencil-square-o", link: "#",
          sub_menu: [
            { title: "Sub-Menu Item 2", icon: "fa-hand-rock-o", link: "#" },
          ] },
        { title: "Menu Item 2", icon: "fa-hand-rock-o", link: "#" },
        { title: "Menu Item 3", icon: "fa-area-chart", link: "#" },
        { title: "Menu Item 4", icon: "fa-pie-chart", link: "#" },
        { title: "Menu Item 5", icon: "fa-line-chart", link: "#" }
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
  /*letter-spacing: 0.03em;*/
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
  font-size:14px;
}
.sidenav-ul a:hover {
  background-color:#222;
  text-decoration:none;
}
/*.sidenav-ul a:visited {
  text-decoration:none;
}*/
.sidenav-ul a li {
  padding:10px 0;
  text-align:left;
}
.sidenav-ul a li > div {
  display:inline-block;
}
.sidenav-ul a li i.fa:first-child {
  position: relative;
  top: 2px;
  /*padding: 0 30px 0 20px;*/
  padding-left:20px;
  font-size: 1.5em;
  width:70px;
}
.sidenav-ul a li i.fa:last-child {
  float: right;
  padding: 0 20px 0 30px;
  font-size: 1.5em;
}
.sidenav-ul a li span {

}
hr.divider {

}
</style>
