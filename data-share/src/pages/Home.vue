<template>
  <div class="home">
    <Header></Header>
    <Tab :current="current"></Tab>
    <div class="content">
      <Crumb :current="current"></Crumb>
      <div class="data_table">

        <div class="data_table_tr">
          <span class="data_table_tr_left">文件名</span>
          <div class="data_table_tr_right">
            <span class="download">下载</span>
            <span class="author">上传者</span>
            <span class="date">创建时间</span>
          </div>
        </div>

        <div class="table_list_item" v-for="(file,index) in dataList" :key="index">
          <div class="item_left">
            <span class="document_name">
              <span class="el-icon-folder"></span>
              {{file.name}}
            </span>
          </div>
          <div class="item_right">
            <span class="download el-icon-download" @click="handleDownload(file.id)"></span>
            <span class="author">{{file.author}}</span>
            <span class="date">{{file.date}}</span>
          </div>
        </div>
        
      </div>
      <el-pagination
        background
        layout="prev, pager, next"
        :total="1000">
      </el-pagination>
    </div>
  </div>
</template>

<script>
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
      current: 'home',
      dataList: []
    };
  },
  methods: {
    getDataList() {
      //发送请求 获取数据
      this.dataList = [
        {
          id: 'dafswf',
          name: '西游记第一章',
          download: 'http://www.baidu.com',
          author: '张飒',
          date: '2020-02-02'
        },
        {
          id: 'dafswsadadf',
          name: '西游记第一章',
          download: 'http://www.baidu.com',
          author: '张飒',
          date: '2020-02-02'
        },
        {
          id: 'dasdaafswsadadf',
          name: '西游记第一章',
          download: 'http://www.baidu.com',
          author: '张飒',
          date: '2020-02-02'
        },
        {
          id: 'asd123212dasdaafswsadadf',
          name: '西游记第一章',
          download: 'http://www.baidu.com',
          author: '张飒',
          date: '2020-02-02'
        },
        
        {
          id: '1sd123212dasdaafswsadadf',
          name: '西游记第一章',
          download: 'http://www.baidu.com',
          author: '张飒',
          date: '2020-02-02'
        },
        {
          id: '2222d123212dasdaafswsadadf',
          name: '阿萨德加拿大',
          download: 'http://www.baidu.com',
          author: '士大夫',
          date: '2020-09-02'
        },
        {
          id: '6575sd123212dasdaafswsadadf',
          name: '阿萨德第一章',
          download: 'http://www.baidu.com',
          author: '实践活动',
          date: '2020-03-02'
        },
      ]
    },
    handleDownload(id) {
      console.log(id);
      //发送请求。。。
    }
  },
  mounted() {
    //获取数据
    this.getDataList()
  }
};
</script>

<style lang="less" scoped>
.home{
  .content{
    padding: 30px 120px;
    .data_table{
      margin: 30px 0;
      .data_table_tr{
        height: 42px;
        width: 100%;
        padding-left: 25px;
        padding-right: 25px;
        border-left: 1px solid #e1e1e1;
        border-top: 1px solid #e1e1e1;
        border-right: 1px solid #e1e1e1;
        background-color: #f4f4f4;
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: #202020;
        font-size: 14px;
        font-weight: 100;
        .data_table_tr_right{
          span{
            display: inline-block;
            text-align: center;
          }
          .download{
            width: 60px;
          }
          .author{
            width: 140px;
          }
          .date{
            width: 100px;
          }
        }
      }
      .table_list_item{
        height: 49px;
        border-bottom: 1px dashed #ccc;
        padding-left: 25px;
        padding-right: 25px;
        cursor: pointer;
        display: flex;
        justify-content: space-between;
        align-items: center;
        &:hover{
          background-color: #f7fbee;
        }
        .item_left{
          .document_name{
            color: #202020;
            font-size: 14px;
            .el-icon-folder{
              margin-right: 5px;
            }
          }
        }
        .item_right{
          span{
            display: inline-block;
            text-align: center;
            color: #333;
            font-size: 14px;
          }
          .download{
            width: 60px;
            font-size: 18px;
            color: #0998ce;
          }
          .author{
            width: 140px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
          }
          .date{
            width: 100px;
          }
        }
      }
    }
  }
}
</style>
