<template>
  <div class="admin">
    <Header></Header>
    <div class="main">
      <Leftnav :index="index"></Leftnav>
      <div class="right_content">
        <div class="right_main">
          <el-timeline>
            <el-timeline-item :timestamp="record.timestamp" placement="top" v-for="record in records" :key="record.id">
              <el-card>
                <h4 class="timeline_title">{{record.fileName}}</h4>
                <p>{{record.user}} <span v-if="record.type=='download'">下载于</span> <span v-if="record.type=='upload'">上传于</span> {{record.date}}</p>
              </el-card>
            </el-timeline-item>
            
          </el-timeline>
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
  name: "Home",
  components: {
    Header,
    Leftnav
  },
  data() {
    return {
      index: '1',
      records: []
    };
  },
  methods: {
    //验证角色 如果不是管理员，无法进入
    validate() {
      const userInfo = util.getUserInfo()
      if (userInfo.role != 'admin') {
        this.$router.replace('/')
      } else {
        //获取日志数据
        this.getRecords()
      }
    },
    //获取日志数据
    getRecords() {
      //发送请求
      //axios...
      //模拟数据
      this.records = [
        {
          id: 'asfdsafwerwe',
          fileName: '水浒传第一张',
          user: '张三',
          type: 'download',
          timestamp: '2020/6/3',
          date: '2020/6/3 20:46'
        },
        {
          id: 'asfdsa345fwerwe',
          fileName: '西域记',
          user: '阿萨德',
          type: 'upload',
          timestamp: '2020/5/3',
          date: '2020/5/3 18:46'
        },
        {
          id: 'hjgdsa345fwerwe',
          fileName: '文件夹测试',
          user: '是的德',
          type: 'upload',
          timestamp: '2020/4/3',
          date: '2020/4/3 12:46'
        },
        {
          id: 'klghjdsa345fwerwe',
          fileName: 'rar文件',
          user: '安抚德',
          type: 'download',
          timestamp: '2019/1/3',
          date: '2019/1/3 12:45'
        }
      ]
    }
  },
  mounted() {
    //验证角色
    this.validate()
  }
};
</script>

<style lang="less" scoped>
.admin {
  .main {
    display: flex;
    .right_content {
      padding-left: 120px;
      padding-top: 40px;
      .right_main {
        width: 800px;
        .timeline_title{
          margin-bottom: 12px;
        }
      }
    }
  }
}
</style>