<template>
  <div class="add">
    <Header></Header>
    <div class="main">
      <Leftnav :index="index"></Leftnav>
      <div class="right_content">
        <div class="right_main">
          <el-form label-position="right" label-width="80px">
            <el-form-item label="名称" required>
              <el-input placeholder="请输入资料名称" v-model="fileName"></el-input>
            </el-form-item>
            <el-form-item label="文件资料" required>
              <el-upload
                class="upload-demo"
                drag
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
                :before-upload="beforeUpload"
                :on-success="onSuccessData"
              >
                <i class="el-icon-upload"></i>
                <div class="el-upload__text">
                  将文件拖到此处，或<em>点击上传</em>
                </div>
              </el-upload>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="handleUploadFile">提交</el-button>
            </el-form-item>
          </el-form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import util from '../util/index'
import Header from "../components/header";
import Leftnav from "../components/left-nav";

export default {
  components: {
    Header,
    Leftnav,
  },
  data() {
    return {
      index: "2",
      fileName: ''
    };
  },
  methods: {
    beforeUpload(file) {
      //如果需要限制文件类型 上传前判断类型 可阻止上传
      console.log(file)
    },
    //上传成功回调
    onSuccessData(response, file, fileList) {
      console.log(response)
      console.log(file)
      console.log(fileList)
    },
    //提交按钮
    handleUploadFile() {
      if (!this.fileName) {
        this.$message({
          showClose: true,
          message: '请输入资料名称',
          type: 'error'
        });
        return
      }
      //发送请求
      //axios...
    },
    //验证角色 如果不是管理员，无法进入
    validate() {
      const userInfo = util.getUserInfo()
      if (userInfo.role != 'admin') {
        this.$router.replace('/')
      }
    },
  },
  mounted() {
    //验证角色
    this.validate()
  }
};
</script>

<style lang="less" scoped>
.add {
  .main {
    display: flex;
    .right_content {
      padding-left: 120px;
      padding-top: 40px;
      .right_main {
        width: 500px;
      }
    }
  }
}
</style>