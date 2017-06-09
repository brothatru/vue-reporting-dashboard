<template>
  <div class="sidenav">
    <ul class="sidenav-ul">
      <div v-for="item in items">
        <a href="javascript:;" :class="{selected: item.selected}" @click="highlight(item);">
          <li>
            <i class="fa" :class="item.icon" aria-hidden="true"></i> <span>{{item.title}}</span> <i class="fa" :class="{'fa-angle-up': item.selected, 'fa-angle-down': !item.selected}" aria-hidden="true"></i></transition>
          </li>
        </a>
        <transition name="slide-fade">
          <ul v-if="item.selected" class="sidenav-sub-menu-ul">
            <a v-for="subItem in item.sub_menu" href="#">
              <li>
                <i class="fa" aria-hidden="true"></i> <span>{{subItem.title}}</span>
              </li>
            </a>
          </ul>
        </transition>
      </div>
      <hr class="divider">
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
            { title: "Sub-Menu Item 1", icon: "fa-hand-rock-o", link: "#" },
          ] },
        { title: "Menu Item 2", icon: "fa-hand-rock-o", link: "#",
          sub_menu: [
            { title: "Sub-Menu Item 1", icon: "fa-hand-rock-o", link: "#" },
          ] },
        { title: "Menu Item 3", icon: "fa-area-chart", link: "#" },
        { title: "Menu Item 4", icon: "fa-pie-chart", link: "#" },
        { title: "Menu Item 5", icon: "fa-line-chart", link: "#" }
      ],
    }
  },
  methods: {
    highlight(item) {
      let vm = this,
          items = vm.items;
      for (let i of items) {
        if (i == item) {
          i.selected = !i.selected;
        }
        else if (i.selected) {
          i.selected = false;
        }
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
a:focus, a:visited, a:hover {
  text-decoration:none;
}
a:hover {
  background-color:#222;
}
a.selected {
  background-color:#222;
  text-decoration:none;
}
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
i.fa-angle-down,
i.fa-angle-up
{
  font-weight:bold;
  float: right;
  padding: 0 25px 0 30px;
  font-size: 1.5em;
}
.sidenav-sub-menu-ul {
  list-style:none;
  padding:0;
}

/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .05s ease;
}
.slide-fade-leave-active {
  transition: all .05s ease;
}
hr.divider {
  margin:0;
  border-top:1px solid #555;
}
</style>
