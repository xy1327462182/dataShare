<template>
  <div class="uploaded">
    <Header></Header>
    <div class="main">
      <Leftnav :index="index"></Leftnav>
      <div class="right_content">
        <div class="right_main">
          <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="date" label="创建时间" width="180">
            </el-table-column>
            <el-table-column prop="name" label="文件名称" width="180">
            </el-table-column>
            <el-table-column prop="author" label="上传者"> </el-table-column>
            <el-table-column label="操作" width="120">
              <template slot-scope="scope">
                <el-button
                  size="mini"
                  type="danger"
                  @click="handleDelete(scope.$index, scope.row)"
                  >删除</el-button
                >
              </template>
            </el-table-column>
          </el-table>
          <el-pagination background layout="prev, pager, next" :total="1000">
          </el-pagination>
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
      index: "3",
      tableData: [],
    };
  },
  methods: {
    //删除
    handleDelete(index, data) {
      console.log(index, data);
      //发送请求...
    },
    getFileList() {
      //发送请求
      //模拟数据
      this.tableData = [
        {
          id: "asdwqadqwe",
          name: "西游记第一章",
          download: "http://www.baidu.com",
          author: "张飒",
          date: "2020-02-02",
        },
        {
          id: "21232sdwqadqwe",
          name: "测试第一章",
          download: "http://www.baidu.com",
          author: "张飒",
          date: "2020-02-02",
        },
        {
          id: "asddfgdfgadqwe",
          name: "阿萨德加拿大",
          download: "http://www.baidu.com",
          author: "士大夫",
          date: "2020-09-02",
        },
        {
          id: "khyktgdwqadqwe",
          name: "阿萨德第一章",
          download: "http://www.baidu.com",
          author: "实践活动",
          date: "2020-03-02",
        },
      ];
    },
    //验证角色 如果不是管理员，无法进入
    validate() {
      const userInfo = util.getUserInfo()
      if (userInfo.role != 'admin') {
        this.$router.replace('/')
      } else {
        //获取数据
        this.getFileList()
      }
    },
  },
  mounted() {
    //验证角色
    this.validate()
  },
};
</script>

<style lang="less" scoped>
.uploaded {
  .main {
    display: flex;
    .right_content {
      padding-left: 120px;
      padding-top: 40px;
      .right_main {
        width: 800px;
        .el-pagination{
          margin-top: 30px;
        }
      }
    }
  }
}
</style>