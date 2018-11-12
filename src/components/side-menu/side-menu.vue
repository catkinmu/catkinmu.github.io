<template>
  <div class="side-menu-wrapper">
    <slot></slot>
    <Menu v-show="!collapsed" width="auto" theme="dark">
      <template v-for="item in list">
        <re-submenu v-if="item.children" :key="`menu_${item.name}`" :name="item.name" :parent="item">
        </re-submenu>
        <menu-item v-else :key="`menu_${item.name}`" :name="item.name">
          <Icon :type="item.icon" />
          {{ item.title }}
        </menu-item>
      </template>
    </Menu>
    <div v-show="collapsed" class="drop-wrapper">
      <template v-for="item in list">
        <re-dropdown v-if="item.children" :show-title="false" :parent="item"></re-dropdown>
        <Tooltip v-else :content="item.title" placement="right" :key="`drop_${item.name}`">
          <span class="drop-menu-span">
            <Icon :type="item.icon" :size="20" />
          </span>
        </Tooltip>
      </template>
    </div>
  </div>
</template>

<script>
import ReSubmenu from './re-submenu'
import ReDropdown from './re-dropdown'
export default {
  name: 'SideMenu',
  components: {
    ReSubmenu,
    ReDropdown
  },
  props: {
    collapsed: {
      type: Boolean,
      default: false
    },
    list: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style lang="less">
.side-menu-wrapper {
  width: 100%;
  .ivu-tooltip,
  .drop-menu-span {
    display: block;
    text-align: center;
    color: #ffffff;
    padding: 5px 0;
    width: 100%;
    cursor: pointer;
  }
  .drop-wrapper {
    & > .ivu-dropdown {
      display: block;
      margin: 0 auto;
      padding: 5px 0;
    }
    & > div:hover {
      background-color: #363e4f;
    }
  }
  .ivu-select-dropdown {
    background-color: #515a6e;
    min-width: 100%;
    .ivu-dropdown {
      border-radius: 4px;

      &:hover {
        background-color: #363e4f;
      }
      &-rel {
        padding: 0 5px;
      }
      &-item {
        padding: 0 5px;
        line-height: 30px;
        color: #ffffff;
        border-radius: 4px;
        &:hover {
          background-color: #363e4f;
        }
      }
    }
  }
}
</style>