<template>
  <div class="login">
    <div class="login-box" v-if="toggleLoginSign">
      <span class="login-title">一张表信息服务平台登录</span>
      <el-button class="login-btn" type="primary">数字证书登录</el-button>
      <span class="login-toggle" @click="toggleLoginSign = !toggleLoginSign">用户名密码登录</span>
      <!-- <el-form :model="loginForm" status-icon :rules="rules" ref="loginForm" label-width="100px" class="demo-ruleForm">
        <el-form-item label="用户名" prop="username">
          <el-input v-model="loginForm.username"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('loginForm')">提交</el-button>
          <el-button @click="resetForm('loginForm')">重置</el-button>
        </el-form-item>
      </el-form> -->
    </div>
    <div class="login-user-psd" v-else>
      <span class="login-title">一张表信息服务平台登录</span>
      <el-form :model="loginForm" :rules="rules" ref="loginForm" class="login-form">
        <el-form-item prop="username" class="username">
          <el-input class="user-inp" v-model="loginForm.username" placeholder="请输入账号"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input class="psd-inp" type="password" v-model="loginForm.password" autocomplete="off" placeholder="请输入密码"></el-input>
        </el-form-item>
      </el-form>
      <span class="login-toggle" @click="toggleLoginSign = !toggleLoginSign">数字证书登录</span>
      <el-button class="login-btn" type="primary" @click="submitForm('loginForm')">登录</el-button>
    </div>
  </div>
</template>

<script>
import { setStorage } from '@/utils/auth'

export default {
  name: 'login',
  components: {

  },
  data () {
    var validateUsername = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('用户名不能为空'))
      }
      callback()
    }

    var validatePass = (rule, value, callback) => {
      if (value === '') {
        return callback(new Error('请输入密码'))
      } else if (value.length >= 6 && value.length <= 8) {
        callback()
      }
      callback(new Error('密码的长度为大于等于6小于等于8'))
    }
    return {
      toggleLoginSign: true,
      loginForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { validator: validateUsername, trigger: 'blur' }
        ],
        password: [
          { validator: validatePass, trigger: 'blur' }
        ]
      }
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
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          setStorage('token', this.loginForm)
          this.$router.push({ path: '/' })
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style lang="scss" scoped>
.login {
  width: 100%;
  height: 100%;
  background: url('../../assets/img/login.png');
  padding: 200px 0 0 880px;
  box-sizing: border-box;
  .login-box {
    width: 590px;
    height: 500px;
    background: #FFFFFF;
    display: flex;
    flex-direction: column;
    .login-title {
      margin: 80px auto 120px;
      font-size: 40px;
      color: #1D304E;
    }
    .login-btn {
      font-size: 26px;
      margin: 0 auto 30px;
      width: 484px;
      height: 68px;
      background: #1D304E;
    }
    .login-toggle {
      padding-right: 53px;
      text-align: end;
      font-size: 20px;
      color: #3C4452;
      cursor: pointer;
    }
  }
  .login-user-psd {
    width: 590px;
    height: 590px;
    background: #FFFFFF;
    display: flex;
    flex-direction: column;
    .login-title {
      margin: 60px auto 66px;
      font-size: 40px;
      color: #1D304E;
    }
    .login-form {
      margin: 0 auto 30px;
      width: 484px;
      .el-form-item {
        margin-bottom: 0 !important;
      }
      .username {
        margin-bottom: 40px !important;
      }
    }
    .login-toggle {
      margin-bottom: 43px;
      padding-right: 53px;
      text-align: end;
      font-size: 20px;
      color: #3C4452;
      cursor: pointer;
    }
    .login-btn {
      font-size: 26px;
      margin: 0 auto 30px;
      width: 484px;
      height: 68px;
      background: #1D304E;
    }
  }
}
.user-inp {
  &::before {
    content: '';
    position: absolute;
    top: 16px;
    left: 25px;
    width: 31px;
    height: 31px;
    background: url('../../assets/img/user.png');
  }
}
.psd-inp {
  &::before {
    content: '';
    position: absolute;
    top: 16px;
    left: 25px;
    width: 31px;
    height: 31px;
    background: url('../../assets/img/psd.png');
  }
}
/deep/.el-input__inner {
  height: 64px;
  font-size: 24px;
  color: #3C4452 !important;
  padding-left: 72px;
}
/deep/.el-input__inner::placeholder {
  color: #3C4452 !important;
}
</style>
