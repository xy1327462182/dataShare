<template>
  <div class="user">
    <Header></Header>
    <Tab :current="current"></Tab>
    <div class="content">
      <Crumb :current="current"></Crumb>
      <div class="user_main">
        <el-tabs tab-position="left">
          <el-tab-pane label="基本信息">
            <div class="user_info_wrap">
              <ul>
                <li class="user_info_list_item">
                  <span>注册时间:</span>
                  <p>2020-02-02 12:00</p>
                </li>
                <li class="user_info_list_item">
                  <span>用户名:</span>
                  <p>{{ userInfo.username }}</p>
                </li>
                <li class="user_info_list_item">
                  <span>角色:</span>
                  <p v-if="userInfo.role != 'admin'">普通用户</p>
                  <p v-if="userInfo.role == 'admin'">管理员</p>
                </li>
              </ul>
            </div>
          </el-tab-pane>
          <el-tab-pane label="修改信息">
            <div class="update_info_wrap">
              <el-input
                v-model="newUsername"
                placeholder="请输入用户名"
              ></el-input>
              <el-button type="primary" @click="updateUname">提交</el-button>
            </div>
          </el-tab-pane>
          <el-tab-pane label="修改密码">
            <div class="update_password_wrap">
              <el-form
                label-position="right"
                label-width="80px"
              >
                <el-form-item label="旧密码">
                  <el-input v-model="oldPassword" show-password placeholder="请输入旧密码"></el-input>
                </el-form-item>
                <el-form-item label="新密码">
                  <el-input v-model="password" show-password placeholder="请输入新密码"></el-input>
                </el-form-item>
                <el-form-item label="确认密码">
                  <el-input v-model="rePassword" show-password placeholder="请再次输入新密码"></el-input>
                </el-form-item>
                <el-form-item>
                  <el-button type="primary" @click="updatePassword">提交</el-button>
                </el-form-item>
              </el-form>
            </div>
          </el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import util from '../util/index'
import Header from "../components/header";
import Tab from "../components/tab";
import Crumb from "../components/bread-crumb";

export default {
  name: "Home",
  components: {
    Header,
    Tab,
    Crumb,
  },
  data() {
    return {
      current: "user",
      userInfo: {},
      newUsername: "",
      oldPassword: '',
      password: '',
      rePassword: ''
    };
  },
  methods: {
    //更新用户名
    updateUname() {
      if (!this.newUsername) {
        this.$message({
          type: 'error',
          message: '请输入内容',
        })
        return
      }
      //发送请求
      //axios...
    },
    //更新密码
    updatePassword() {
      if (!oldPassword) {
        this.$message({
          type: 'error',
          message: '请输入旧密码',
        })
        return
      }
      if (!password) {
        this.$message({
          type: 'error',
          message: '请输入新密码',
        })
        return
      }
      if (!rePassword) {
        this.$message({
          type: 'error',
          message: '请再次输入新密码',
        })
        return
      }
      if (this.rePassword != this.password) {
        this.$message({
          type: 'error',
          message: '两次输入密码不一致',
        })
        return
      }
      //发送请求
      //axios....
    },
    getUserInfo() {
      //模拟数据
      const userInfo = util.getUserInfo()
      this.userInfo = userInfo
    }
  },
  mounted() {
    //获取用户信息
    this.getUserInfo()
  }
};
</script>

<style lang="less" scoped>
.user {
  .content {
    padding-left: 120px;
    padding-right: 120px;
    padding-top: 30px;
    .user_main {
      margin-top: 50px;
      .user_info_wrap {
        margin-left: 50px;
        .user_info_list_item {
          height: 60px;
          border-bottom: 1px dashed #ccc;
          padding-left: 50px;
          display: flex;
          align-items: center;
          span {
            font-size: 18px;
            margin-right: 18px;
          }
          p {
            color: #666;
          }
        }
      }
      .update_info_wrap {
        width: 440px;
        margin-left: 50px;
        margin-top: 30px;
        display: flex;
        flex-flow: column nowrap;
        justify-content: space-between;
        align-items: center;
        .el-input {
          margin-bottom: 30px;
        }
      }
      .update_password_wrap{
        width: 440px;
        margin-left: 50px;
      }
    }
  }
}
</style>