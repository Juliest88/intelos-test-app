<template>
  <n-menu class="menu-container full-height" v-model="activeKey" :options="menuOptions" />
</template>

<script>
import { h } from 'vue'
import { NIcon, NMenu } from 'naive-ui'
import IconCampaign from './icons/IconCampaign.vue'
import IconCases from './icons/IconCases.vue'
import IconGroup from './icons/IconGroup.vue'
import IconManageSearch from './icons/IconManageSearch.vue'
import IconMap from './icons/IconMap.vue'
import IconMenu from './icons/IconMenu.vue'
import IconSearchInsights from './icons/IconSearchInsights.vue'

export default {
  components: {
    NMenu,
    NIcon,
  },
  data() {
    return {
      activeKey: 'menu',
      collapsed: false,
      menuOptions: [
        { key: 'menu', icon: this.renderIcon(IconMenu) },
        { key: 'map', icon: this.renderIcon(IconMap) },
        { key: 'group', icon: this.renderIcon(IconGroup) },
        { key: 'campaign', icon: this.renderIcon(IconCampaign) },
        { key: 'searchInsights', icon: this.renderIcon(IconSearchInsights) },
        { key: 'cases', icon: this.renderIcon(IconCases) },
        { key: 'manageSearch', icon: this.renderIcon(IconManageSearch) },
      ],
    }
  },
  methods: {
    renderIcon(icon) {
      return () => h(NIcon, null, { default: () => h(icon) })
    },
  },
}
</script>

<style scoped>
.menu-container {
  border-right: 1px solid #d1d5db;
}
</style>
