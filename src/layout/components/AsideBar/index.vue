<template>
  <div class="aside-bar">
    <el-menu
      class="el-menu-vertical-demo"
      router
      :collapse="isCollapse"
      :default-active="activeMenu"
      :background-color="variables.menuBg"
      :text-color="variables.menuText"
      :active-text-color="variables.menuActiveText"
      :collapse-transition="false"
    >
      <menu-item
        v-for="route in dealRoutes"
        :key="route.path"
        :item="route"
      ></menu-item>
    </el-menu>
  </div>
</template>

<script>
import MenuItem from '@/layout/components/AsideBar/MenuItem'
import variables from '@/styles/variables.scss'

import { mapGetters } from 'vuex'

export default {
  name: 'aside-bar',
  components: {
    MenuItem
  },
  data () {
    return {
      routes: []
    }
  },
  computed: {
    ...mapGetters([
      'isCollapse'
    ]),
    dealRoutes () {
      return this.$store.getters.routes.filter(route => route.hidden !== true)
    },
    activeMenu () {
      return this.$route.path
    },
    variables () {
      return variables
    }
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

/deep/.el-menu {
  border-right: none;
}
</style>
