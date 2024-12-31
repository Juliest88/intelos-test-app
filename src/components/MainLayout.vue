<script setup>
import { NLayout, NLayoutContent, NLayoutSider, NSpace } from 'naive-ui'
import MainContent from './MainContent.vue'
import NavBar from './NavBar.vue'
</script>

<template>
  <n-space>
    <n-layout class="full-page" has-sider>
      <n-layout-sider :width="90">
        <NavBar />
      </n-layout-sider>
      <n-layout-content
        content-style="padding: 24px; background: #f2f2f3; width: 100%; height: 100%;"
      >
        <MainContent />
      </n-layout-content>
    </n-layout>
  </n-space>
</template>

<style scoped></style>
