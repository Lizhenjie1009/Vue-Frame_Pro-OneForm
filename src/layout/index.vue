<template>
  <div class="layout">
    <el-container style="height: 100%">
      <el-header>
        <nav-bar></nav-bar>
      </el-header>
      <!-- body -->
      <el-container>
        <!-- 侧边栏 -->
        <!-- <el-aside :width='!$store.getters.isCollapse ? "240px" : "64px"'> -->
        <el-aside>
          <aside-bar></aside-bar>
        </el-aside>

        <!-- 导航栏 -->
        <!-- <el-header>
          <nav-bar></nav-bar>
        </el-header> -->

        <!-- 主体区域 -->
        <el-main>
          <!-- <crumbs-bar></crumbs-bar> -->
          <!-- 导航标签 -->
          <!-- <tags-bar></tags-bar> -->
          <!-- 内容区域 -->
          <transition name="fade-transform" mode="out-in">
            <router-view></router-view>
          </transition>
        </el-main>

      </el-container>
    </el-container>
  </div>
</template>

<script>
import AsideBar from './components/AsideBar'
import CrumbsBar from './components/CrumbsBar'
import NavBar from './components/NavBar'
import TagsBar from './components/TagsBar'

export default {
  components: {
    AsideBar,
    CrumbsBar,
    NavBar,
    TagsBar
  },
  data () {
    return {

    }
  },
  computed: {

  },
  watch: {

  },
  created () {

  },
  mounted () {

  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
.layout {
  width: 100%;
  height: 100%;
}
aside {
  width: 300px;
  margin-bottom: 0;
  padding: 0;
  background: #1D304E;
  box-sizing: border-box;
}
.el-header {
  padding: 0 !important;
  // height: 83px;
  background-color: #BD0B00;
  height: 83px !important;
}

.el-main {
  padding: 0;
}

.fade-transform-leave-active,
.fade-transform-enter-active {
  transition: all .5s;
}
.fade-transform-enter {
  opacity: 0;
  transform: translateX(-30px);
}
.fade-transform-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

</style>
