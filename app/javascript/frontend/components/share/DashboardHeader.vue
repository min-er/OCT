<template>
  <el-row class="row-bg" type="flex" justify="space-around" align="middle">
    <el-col :span="4"
      ><h1><a id="logo" href="#">OCT</a></h1></el-col
    >
    <el-col :span="8">
      <el-menu
        :data="menuData"
        :default-active="activeIndex"
        class="el-menu-demo"
        mode="horizontal"
        @select="handleSelect"
      >
        <el-menu-item index="1">我的课程</el-menu-item>
        <el-menu-item index="2">课后学习</el-menu-item>
        <!-- <el-submenu index="2">
              <template slot="title">课后学习</template>
              <el-menu-item index="2-1">选项1</el-menu-item>
              <el-menu-item index="2-2">选项2</el-menu-item>
              <el-menu-item index="2-3">选项3</el-menu-item>
              <el-submenu index="2-4">
                <template slot="title">资讯</template>
                <el-menu-item index="2-4-1">选项1</el-menu-item>
                <el-menu-item index="2-4-2">选项2</el-menu-item>
                <el-menu-item index="2-4-3">选项3</el-menu-item>
              </el-submenu>
            </el-submenu> -->
        <el-menu-item index="3">资讯</el-menu-item>
      </el-menu>
    </el-col>
    <el-col :span="12" class="right-menu">
      <!-- TODO: 点击弹出工具栏 -->
      <!-- <el-menu
            class="el-right-sub-menu"
            :data="rightSubMenuData"
            :collapse="isRightSubMenuCollapse"
          >
            <el-button class="right-menu-icons" type="text"
              ><i class="el-icon-menu"></i></el-button
            ><el-button class="right-menu-icons" type="text"
              ><i class="el-icon-menu"></i></el-button
            ><el-button class="right-menu-icons" type="text"
              ><i class="el-icon-menu"></i></el-button
            ><el-button class="right-menu-icons" type="text"
              ><i class="el-icon-menu"></i
            ></el-button>
          </el-menu> -->
      <el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-edit"></i></el-button
      ><el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-folder-opened"></i
      ></el-button>
      <el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-date"></i></el-button
      ><el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-finished"></i></el-button
      ><el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-data-analysis"></i></el-button
      ><el-button class="right-menu-icons right-tools" type="text"
        ><i class="el-icon-video-camera"></i
      ></el-button>
      <el-button
        class="right-menu-icons"
        type="text"
        @click="handleRightSubMenu"
        ><i class="el-icon-menu"></i
      ></el-button>
      <el-button class="right-menu-icons" type="text"
        ><i class="el-icon-refresh"></i
      ></el-button>
      <el-button class="right-menu-icons" type="text"
        ><i class="el-icon-bell"></i
      ></el-button>
      <el-button class="right-menu-icons" type="text"
        ><el-avatar :size="27" :src="circleUrl"></el-avatar
      ></el-button>
    </el-col>
  </el-row>
</template>

<style>
.el-header {
  text-align: center;
  padding: 0px;
  min-width: 900px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 0 6px rgba(0, 0, 0, 0.04);
}

#logo {
  color: #409eff;
  text-decoration: none;
}

.right-menu-icons {
  font-size: 24px;
  padding: 10px;
}

.right-tools {
  visibility: hidden;
}
</style>


<script>

export default {
  name: "DashboardHeader",
  methods: {
    get_bodyHeight () {//动态获取浏览器高度
      const that = this
      window.onresize = () => {
        return (() => {
          window.fullHeight = document.documentElement.clientHeight
          that.fullHeight = window.fullHeight
        })()
      }
    },
    handleSelect (key, keyPath) {
      console.log(key, keyPath)
    },
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    },
    handleRightSubMenu () {
      isRightSubMenuCollapse = !isRightSubMenuCollapse
    }
  },
  watch: {
    fullHeight (val) {//监控浏览器高度变化
      if (!this.timer) {
        this.fullHeight = val
        this.timer = true
        let that = this
        setTimeout(function () {
          that.timer = false
        }, 400)
      }
    }
  },
  mounted () {
    this.get_bodyHeight()
  },
  data () {
    return {
      circleUrl: "https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png",
      fullHeight: document.documentElement.clientHeight,
      leftMenuData: [{
        isCollapse: true
      }],
      rightSubMenuData: [{
        isRightSubMenuCollapse: true
      }],
      menuData: [{
        activeIndex: '1',
        activeIndex2: '1'
      }]
    }
  }
}
</script>
