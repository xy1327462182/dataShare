<template>
  <div class="cus_tabs">
    <ul>
      <li :class="current == 'home' ? 'tabs_title_active' : ''">
        <router-link tag="div" class="tabs_title_item" to="/"
          >资料大厅</router-link
        >
      </li>
      <li :class="current == 'user' ? 'tabs_title_active' : ''">
        <router-link tag="div" class="tabs_title_item" to="/user"
          >个人中心</router-link
        >
      </li>
    </ul>
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
.cus_tabs {
  height: 70px;
  background-color: #f5f7fa;
  border-bottom: 1px solid #ccc;
  ul {
    height: 70px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding-right: 85px;
    li {
      background-color: #ecf5ff;
      color: #409eff;
      border: 1px solid #d9ecff;
      border-radius: 4px;
      margin-left: 20px;
      cursor: pointer;
      .tabs_title_item{
        width: 100%;
        height: 100%;
        padding: 5px 10px;
      }
    }
    .tabs_title_active {
      background-color: #409eff;
      color: #fff;
      border: 1px solid #d9ecff;
    }
  }
}
</style>