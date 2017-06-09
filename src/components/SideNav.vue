<template>
  <div class="sidenav">
    <ul class="sidenav-ul">
      <div v-for="item in items">
        <a href="javascript:;" :class="{selected: item.selected}" @click="highlight(item);">
          <li>
            <i class="fa" :class="item.icon" aria-hidden="true"></i> <span>{{item.title}}</span> <i class="fa fa-angle-down" aria-hidden="true"></i>
          </li>
        </a>
        <transition name="slide-fade">
          <ul v-if="item.selected" class="sidenav-sub-menu-ul">
            <a v-for="subItem in item.sub_menu" href="#">
              <li>
                <i class="fa" aria-hidden="true"></i> <span>{{item.title}}</span>
              </li>
            </a>
          </ul>
        </transition>
      </div>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SideNav',
  components: {},
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
      ],
    }
  },
  methods: {
    highlight(item) {
      // console.log(item.title + ' clicked!');
      this.clearSelected();
      item.selected = !item.selected;
    },
    clearSelected() {
      let items = this.items;
      for (let item of items) {
        item.selected = false;
      }
    }
  },
  created() {
    let vm = this;
    for (let item of vm.items) {
      // when dynamically adding reactive data, need to use vue.set, otherwise changes won't propagate
      vm.$set(item, 'selected', false);
    }
  },
  mounted() {
    console.log('sidenav loaded');
    console.log(this.items);
  }
}
</script>

<style>
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
}
.sidenav-ul {
  border:1px red dashed;
  width:100%;
  height:100%;
  list-style:none;
  padding-left:0;
}
.sidenav-ul a {
  display: block;
  color:#fff;
  font-size:14px;
}
/*.sidenav-ul > a:hover {*/
a.selected {
  background-color:#222;
  text-decoration:none;
}
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
  padding-left:20px;
  font-size: 1.5em;
  width:70px;
}
.sidenav-ul a li i.fa-angle-down {
  float: right;
  padding: 0 20px 0 30px;
  font-size: 1.5em;
}
.sidenav-ul a li span {

}
.sidenav-sub-menu-ul {
  list-style:none;
  padding:0;
  margin-top:10px;
}

/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .05s ease;
}
.slide-fade-leave-active {
  transition: all .05s ease;
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for <2.1.8 */ {
  /*transform: translateY(-10px);*/
  /*opacity: 0;*/
}
.slide-fade-leave-to {
  /*transform: translateY(-10px);*/
}
hr.divider {

}
</style>
