<template>
  <div class="cus_breadCrumb">
    <span class="cus_breadCrumb_item" v-show="current=='home'">资料大厅</span>
    <span class="cus_breadCrumb_item" v-show="current=='user'">个人中心</span>
  </div>
</template>

<script>
export default {
  data() {
    return {

    }
  },
  props: {
    current: {
      type: String,
      default: 'home'
    }
  }
};
</script>

<style lang="less" scoped>
.cus_breadCrumb {
  width: 100%;
  height: 40px;
  border-bottom: 2px solid #d9d9d9;
  display: flex;
  align-items: center;
  .cus_breadCrumb_item {
    height: 38px;
    line-height: 38px;
    border-bottom: 2px solid #409eff;
    font-size: 18px;
    padding-left: 10px;
    padding-right: 10px;
    margin: 5px;
  }
}
</style>