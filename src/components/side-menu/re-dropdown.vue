<template>
  <Dropdown placement="right-start" style="width:auto;min-width:100%">
    <span class="drop-menu-span" :style="titleStyle">
      <Icon :type="parent.icon" :size="20" />
      <span v-if="showTitle">{{ parent.title }}</span>
    </span>
    <DropdownMenu slot="list">
      <template v-for="item in parent.children">
        <re-dropdown v-if="item.children" :key="`drop_${item.name}`" :parent="item"></re-dropdown>
        <DropdownItem v-else :key="`drop_${item.name}`" :name="item.name">
          <Icon :type="item.icon" :size="20" />
          {{ item.title }}
        </DropdownItem>
      </template>
    </DropdownMenu>
  </Dropdown>
</template>

<script>
export default {
  name: 'ReDropdown',
  props: {
    parent: {
      type: Object,
      default: () => ({})
    },
    showTitle: {
      type: Boolean,
      default: true
    }
  },
  computed: {
    titleStyle () {
      return {
        textAlign: this.showTitle ? 'left' : 'center'
        // paddingLeft: this.showTitle ? '15px' : ''
      }
    }
  }
}
</script>

<style lang="" scoped>
</style>