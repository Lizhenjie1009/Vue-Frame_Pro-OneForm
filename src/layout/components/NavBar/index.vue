<template>
  <div class="nav-bar">
    <div class="logo"></div>
    <div class="user" @click='logout'>
      张三三
    </div>
  </div>
</template>

<script>
import { setStorage } from '@/utils/auth'

export default {
  name: 'nav-bar',
  components: {

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
    logout () {
      this.$confirm('是否要退出登录?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        this.$message({
          type: 'success',
          message: '退出成功!'
        })
        setStorage('token', '')
        this.$router.replace('/login')
      }).catch(() => {
        this.$message({
          type: 'info',
          message: '已取消退出'
        })
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-bar {
  display: flex;
  justify-content: space-between;
}
.logo {
  margin: 22px 0 0 28px;
  width: 304px;
  height: 39px;
  background: url('../../../assets/img/logo.png');
}
.user {
  margin: 27px 30px 0 0;
  width: 100px;
  height: 28px;
  color: #fff;
  font-size: 20px;
  position: relative;
  &::before {
    content: '';
    position: absolute;
    top: -5px;
    left: -32px;
    width: 30px;
    height: 30px;
    background: url('../../../assets/img/logouser.png');
  }
}
</style>
