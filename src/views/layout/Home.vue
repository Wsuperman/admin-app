<template>
  <div class="home-container">
    <!-- 左边列表区域 -->
    <div class="menu-list">
      <a-menu
        :default-selected-keys="['1']"
        :default-open-keys="['sub1']"
        mode="inline"
        theme="dark"
        :inline-collapsed="collapsed"
      >
        <a-menu-item key="1">
          <a-icon type="pie-chart" />
          <span>Option 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="desktop" />
          <span>Option 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="inbox" />
          <span>Option 3</span>
        </a-menu-item>
        <a-sub-menu key="sub1">
          <span slot="title"
            ><a-icon type="mail" /><span>Navigation One</span></span
          >
          <a-menu-item key="5"> Option 5 </a-menu-item>
          <a-menu-item key="6"> Option 6 </a-menu-item>
          <a-menu-item key="7"> Option 7 </a-menu-item>
          <a-menu-item key="8"> Option 8 </a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub2">
          <span slot="title"
            ><a-icon type="appstore" /><span>Navigation Two</span></span
          >
          <a-menu-item key="9"> Option 9 </a-menu-item>
          <a-menu-item key="10"> Option 10 </a-menu-item>
          <a-sub-menu key="sub3" title="Submenu">
            <a-menu-item key="11"> Option 11 </a-menu-item>
            <a-menu-item key="12"> Option 12 </a-menu-item>
          </a-sub-menu>
        </a-sub-menu>
      </a-menu>
    </div>

    <!-- 右边区域 -->
    <div :class="{ 'mian-app': true, 'menu-unfold': collapsed }">
      <!-- 顶部区域 -->
      <div class="menu-header">
        <!-- 点击按钮 -->
        <a-button
          type="primary"
          style="margin-bottom: 16px"
          @click="toggleCollapsed"
        >
          <a-icon :type="collapsed ? 'menu-unfold' : 'menu-fold'" />
        </a-button>
        <!-- 面包屑 -->
        <div class="breadcrumb">
          <a-breadcrumb>
            <a-breadcrumb-item>首页</a-breadcrumb-item>
            <a-breadcrumb-item><a href="">统计</a></a-breadcrumb-item>
            >
          </a-breadcrumb>
        </div>
        <!-- 用户信息 -->
        <div class="user-info">
          <li>
            欢迎weiweibin
            <a-icon type="down" />
          </li>
          <li>退出</li>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false,
    };
  },
  methods: {
    toggleCollapsed() {
      this.collapsed = !this.collapsed;
    },
  },
};
</script>

<style lang="less">
.home-container {
  .menu-list {
    width: 180px;
    position: fixed; //让左侧区域固定位置
    height: 100%;
    .ant-menu {
      height: 100%;
    }
  }
  .mian-app {
    margin-left: 180px; // 导航按钮移动到右边区域
    transition: all 0.3s; // 动画效果，0.3秒完成，比较柔和一些
    &.menu-unfold {
      margin-left: 80px;
    }
    .menu-header {
      height: 50px;
      line-height: 50px;
      border-bottom: 1px solid #eee;
      padding-left: 10px;
      padding-right: 20px;
      .breadcrumb {
        display: inline-block;
        margin-left: 20px;
      }
      .user-info {
        float: right;
        text-align: center; // 文本居中
        cursor: pointer; // 鼠标样式
        li:not(:first-child) {
          // 不是第一个的li
          display: none;
          // 当前的元素鼠标移入后样式变化
          &:hover {
            background-color: #eee;
            color: #999;
            font-weight: 700;
          }
        }
        li {
          padding: 0 20px;
        }
        // 当鼠标移过去的时候所有li都显示
        &:hover {
          li {
            display: block;
          }
        }
      }
    }
  }
}
</style>