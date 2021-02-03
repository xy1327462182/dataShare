<template>
  <div class="left_nav">
    <el-menu
      :defaultActive="index"
      background-color="#f8f9fa"
      text-color="#333"
      active-text-color="#409eff"
    >
      <router-link to="/admin">
        <el-menu-item index="1">
          <i class="el-icon-s-marketing"></i>
          <!-- <i class="el-icon-s-home"></i> -->
          <span slot="title">日志记录</span>
        </el-menu-item>
      </router-link>

      <router-link to="/addfile">
        <el-menu-item index="2">
          <i class="el-icon-upload"></i>
          <span slot="title">上传资料</span>
        </el-menu-item>
      </router-link>

      <router-link to="/uploaded">
        <el-menu-item index="3">
          <i class="el-icon-s-claim"></i>
          <span slot="title">已上传</span>
        </el-menu-item>
      </router-link>
    </el-menu>
  </div>
</template>

<script>
export default {
  props: {
    index: {
      type: String,
      default: "1",
    },
  },
};
</script>

<style lang="less" scoped>
.left_nav {
  width: 200px;
  height: 100vh;
  background-color: #f8f9fa;
  color: #333;
  text-align: center;
  line-height: 200px;
}
</style>