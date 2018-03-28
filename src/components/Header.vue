<template lang="html">
<div class="header navbar animated">
  <div class="container">
    <el-menu
      :default-active="$route.path"
      router
      class="el-menu-demo"
      mode="horizontal"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-menu-item index="/blog"><i class="fa fa-home"></i>首页</el-menu-item>
      <el-submenu index="2">
        <template slot="title"><i class="fa fa-cog"></i>归档</template>
        <el-menu-item :index="item.tag" v-for="(item, index) in tags" :key="index" @click="getOne(item.tag)">{{item.tag}}</el-menu-item>
      </el-submenu>
      <el-menu-item index="/messages"><i class="fa fa-comment"></i>留言</el-menu-item>
      <el-menu-item index="/about"><i class="fa fa-user"></i>关于</el-menu-item>
    </el-menu>
  </div>
</div>
</template>

<script>
// 实现导航条的自动显示
import Headroom from 'headroom.js'
import { unique } from '@/assets/js/unique';
import axios from 'axios'
export default {
  data () {
    return {
      tags: [],
    }
  },
  methods: {
    getTags () {
      axios.get("/api/articleTags").then((result)=>{
        let res = result.data
        if (res.status == '0') {
          this.tags = res.result
          this.tags = unique(this.tags)
          this.$emit('shareTags', this.tags)
        } else {
          this.tags = ["未获取到数据"]
        }
      })
    },
    getOne (tag) {
      this.$emit('shareOne', tag)
      this.$router.push({path:'/blog'})
    }
  },
  mounted () {
    var myElement = document.querySelector(".header");
    // construct an instance of Headroom, passing the element
    var headroom  = new Headroom(myElement, {
      "tolerance": 1,
      "offset": 10,
      "classes": {
        "initial": "animated",
        "pinned": "slideDown",
        "unpinned": "slideUp"
      }
    });
    headroom.init();
    this.getTags()
  }
}
</script>
<style lang="less" scoped>
.el-menu--horizontal{
  border-bottom: none;
}
.el-submenu__title i,.el-menu-item i{
  color: #fff;
}
.navbar {
  left: 0;
  right: 0;
  top: 0;
  position: fixed;
  z-index: 3;
  background: rgb(84, 92, 100);
}
/*导航条动画*/
.animated {
    animation-duration: 0.5s;
    animation-fill-mode: both;
}
.animated.slideDown {
    -webkit-animation-name: slideDown;
    -moz-animation-name: slideDown;
    -o-animation-name: slideDown;
    animation-name: slideDown;
}
.animated.slideUp {
    -webkit-animation-name: slideUp;
    -moz-animation-name: slideUp;
    -o-animation-name: slideUp;
    animation-name: slideUp;
}
@keyframes slideDown {
  0% {
    transform: translateY(-5em);
  }
  100% {
    transform: translateY(0);
  }
}
@keyframes slideUp {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-5em);
  }
}
</style>

