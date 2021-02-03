<template>
  <div class="login">
    <h2 class="title">欢迎注册资料分享平台</h2>
    <div class="login_wrap">
      <el-form label-position="right" label-width="80px">
        <el-form-item label="用户名" required>
          <el-input placeholder="请输入用户名" v-model="username"></el-input>
        </el-form-item>
        <el-form-item label="密码" required>
          <el-input
            placeholder="请输入密码"
            v-model="pwd"
            show-password
          ></el-input>
        </el-form-item>
        <el-form-item label="重复密码" required>
          <el-input
            placeholder="请再次输入密码"
            v-model="repwd"
            show-password
          ></el-input>
        </el-form-item>
      </el-form>
      <el-button type="primary" :loading="false" @click="handleRegister"
        >注册</el-button
      >
    </div>
    <div class="none_account">已有账号，<router-link to="/login"><el-tag>去登录</el-tag></router-link></div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      username: '',
      pwd: '',
      repwd: ''
    }
  },
  methods: {
    //注册按钮点击
    handleRegister() {
      //验证表单登录信息
      const result = this.validate()
      if (result) {
        //发送注册请求
        //axios...
        this.$message({
          showClose: true,
          message: '发送注册请求',
          type: 'success'
        });
      }
    },
    validate() {
      if (!this.username) {
        this.$message({
          showClose: true,
          message: '请输入用户名',
          type: 'error'
        });
        return false
      }
      if (!this.pwd) {
        this.$message({
          showClose: true,
          message: '请输入密码',
          type: 'error'
        });
        return false
      }
      if (!this.repwd) {
        this.$message({
          showClose: true,
          message: '请输入密码',
          type: 'error'
        });
        return false
      }
      if (this.repwd != this.pwd) {
        this.$message({
          showClose: true,
          message: '两次密码不一致',
          type: 'error'
        });
        return false
      }
      return true
    }
  }
};
</script>

<style lang="less" scoped>
.login {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  width: 100%;
  height: 100vh;
  background: url(../assets/login-bg.svg);
  background-color: #109ad6;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  .title {
    text-align: center;
    color: #fff;
    font-size: 40px;
    font-weight: 700;
    margin-top: 90px;
  }
  .login_wrap {
    margin-top: 60px;
    // position: absolute;
    // left: 50%;
    // top: 70px;
    // transform: translate(-50%);
    width: 500px;
    padding: 30px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
    box-sizing: border-box;
    text-align: center;
    .el-form {
      margin-top: 30px;
    }
    .el-button {
      margin-top: 30px;
    }
    
  }
  .none_account{
    margin-top: 40px;
    color: #333;
  }
}
</style>