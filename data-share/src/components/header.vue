<template>
  <div>
    <div class="top_bar">
      <h1 class="title"><a href="/">资料分享平台</a></h1>
      <div class="user_wrap">
        <el-dropdown trigger="click" @command="handleClick">
          <span class="el-dropdown-link">
            {{ userInfo.username }}
            <i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command="user">个人中心</el-dropdown-item>
            <el-dropdown-item command="admin" v-if="userInfo.role == 'admin'">管理员中心</el-dropdown-item>
            <el-dropdown-item command="logout">退出登录</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </div>
  </div>
</template>

<script>
import util from '../util/index'

export default {
  data() {
    return {
      userInfo: {}
    };
  },
  methods: {
    handleClick(command) {
      if (command == "logout") {
        console.log('logout..');
        //发送请求
        //axios...
      } else if (command == "user") {
        // console.log('user..');
        this.$router.push('/user')
      } else if (command == "admin") {
        //去管理员页面
        this.$router.push('/admin')
      }
    },
    //获取用户信息
    getUserInfo() {
      //模拟数据
      this.userInfo = util.getUserInfo()
    }
  },
  created() {
    //获取登录用户的信息
    this.getUserInfo()
  }
};
</script>

<style lang="less" scoped>
.top_bar {
  height: 60px;
  background: linear-gradient(45deg, #1278f6, #00b4aa 50%, #1278f6);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  .title {
    font-size: 20px;
    color: #fff;
    letter-spacing: 2px;
    background-color: rgba(0, 0, 0, 0);
    cursor: pointer;
  }
  .user_wrap {
    .el-dropdown-link {
      color: #fff;
      cursor: pointer;
      .el-icon-arrow-down {
        font-size: 12px;
      }
    }
  }
}
</style>