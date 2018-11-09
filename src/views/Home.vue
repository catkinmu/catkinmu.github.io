<template>
  <Layout class="layout">
    <Header class="layout-header">
      <div class="layout-header-logo">
        <img src="../assets/img/oalogo.png" alt="logo">
        <span>办公系统模型实例</span>
      </div>
      <Menu class="layout-header-nav" mode="horizontal" theme="dark">
        <menu-item name="1">
          <Icon type="md-mail" />10条
        </menu-item>
        <menu-item name="2">
          <Icon type="md-refresh" />刷新
        </menu-item>
        <Submenu name="3">
          <template slot="title">
            <Icon type="md-construct" />设置
          </template>
          <menu-group title="外观">
            <menu-item name="3-1">选择皮肤</menu-item>
            <menu-item name="3-2">图标菜单</menu-item>
          </menu-group>
          <menu-group title="框架">
            <menu-item name="3-3">政务桌面</menu-item>
          </menu-group>
        </Submenu>
        <Submenu name="4">
          <template slot="title">
            <img class="head-img" src="../assets/head-img/02.jpg" alt="头像">
            管理员
          </template>
          <menu-item name="4-1">个人资料</menu-item>
          <menu-item name="4-2">修改密码</menu-item>
        </Submenu>
        <menu-item name="5">
          <Icon type="md-log-out" />退出
        </menu-item>
      </Menu>
    </Header>
    <Layout>
      <Sider ref="side" hide-trigger :width="140" collapsible :collapsed-width="40" v-model="isCollapsed">
        <div class="menu-icon-wrap" @click="collapsedSider">
          <Icon :class="rotateIcon" type="md-menu" size="24" />
        </div>
        <!-- <side-menu active-name="1-1" theme="dark" width="auto" :class="sidemenuClasses"></side-menu> -->
        <Menu active-name="1-1" theme="dark" width="auto" :class="sidemenuClasses">
          <menu-item name="1-1">
            <Icon type="ios-navigate" />
            <span>Option 1</span>
          </menu-item>
          <menu-item name="1-2">
            <Icon type="ios-search" />
            <span>Option 2</span>
          </menu-item>
          <menu-item name="1-3">
            <Icon type="ios-settings" />
            <span>Option 3</span>
          </menu-item>
        </Menu>
      </Sider>
      <Content>
        <Layout style="height:100%">
          <Header class="tag-nav-wrapper">
            tag-nav-wrapper
          </Header>
          <Content class="layout-content">
            Content
          </Content>
        </Layout>
      </Content>
    </Layout>
  </Layout>
</template>
<script>
import SideMenu from '_c/side-menu'
export default {
  components: {
    SideMenu
  },
  data () {
    return {
      isCollapsed: false
    }
  },
  computed: {
    rotateIcon () {
      return [
        'menu-icon',
        this.isCollapsed ? 'rotate-icon' : ''
      ]
    },
    sidemenuClasses () {
      return ['side-menu', this.isCollapsed ? 'collapsed-menu' : '']
    }
  },
  methods: {
    collapsedSider () {
      this.$refs.side.toggleCollapse()
    }
  }
}
</script>
<style scoped lang="less">
@headerHeight: 40px;
.layout {
  height: 100%;
  color: #fff;
  &-header {
    padding: 0 10px;
    height: @headerHeight;
    line-height: @headerHeight;
    &-logo {
      float: left;
      height: @headerHeight;
      img {
        float: left;
        margin: 5px 10px 5px 5px;
        width: @headerHeight - 10;
        height: @headerHeight - 10;
      }
      span {
        float: left;
        font-size: 18px;
        color: #00bcf2;
      }
    }
    &-nav {
      float: right;
      height: @headerHeight;
      li {
        line-height: @headerHeight;
        padding: 0 10px;
      }
    }
    .head-img {
      float: left;
      margin: 5px;
      border-radius: 50%;
      width: @headerHeight - 10;
      height: @headerHeight - 10;
    }
  }
}
.menu-icon-wrap {
  height: 35px;
  line-height: 35px;
  text-align: center;
  background: #808695;
  cursor: pointer;
  .menu-icon {
    transition: all 0.3s;
  }
  .rotate-icon {
    transform: rotate(-90deg);
  }
}
.side-menu {
  li {
    padding: 10px 5px;
    position: relative;
    padding-left: 25px;
    font-size: 14px;
    line-height: 20px;
    span {
      display: block;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      transition: width 0.2s ease 0.2s;
    }
    i {
      position: absolute;
      left: 5px;
      margin: 0;
      line-height: 20px;
      // transform: translateX(0px);
      transition: font-size 0.2s ease;
      font-size: 18px;
    }
  }
  &.collapsed-menu {
    li {
      span {
        width: 0px;
        transition: width 0.2s ease;
      }
      i {
        left: 50%;
        transform: translateX(-50%);
        transition: font-size 0.2s linear 0.4s, left 0.2s linear 0.4s, transform 0.2s linear 0.4s;
        font-size: 22px;
      }
    }
  }
}
.tag-nav-wrapper {
  height: 35px;
  padding: 0;
  line-height: 35px;
  background: #d58181;
  box-shadow: 0 1px 1px rgba(255, 255, 255, 0.1);
}
.layout-content {
  margin: 10px;
  padding: 10px;
  background: #ffffff;
  color: #333333;
}
</style>