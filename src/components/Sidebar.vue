<template>
<el-row class="h-full">
    <el-col>
      <h5 class="mb-2 bg-blue-500">Default colors</h5>
      <el-menu
        default-active="2"
      >
        <el-sub-menu index="1">
          <template #title>
            <el-icon><location /></el-icon>
            <span>FRED</span>
          </template>
          <el-menu-item-group title="Group One">
            <el-menu-item index="1-1">item one</el-menu-item>
            <el-menu-item index="1-2">item two</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="Group Two">
            <el-menu-item index="1-3">item three</el-menu-item>
          </el-menu-item-group>
          <el-sub-menu index="1-4">
            <template #title>item four</template>
            <el-menu-item index="1-4-1">item one</el-menu-item>
          </el-sub-menu>
        </el-sub-menu>
      </el-menu>
    </el-col>
</el-row>
</template>

<script setup>
import { ElMessage } from 'element-plus'
import {
  Document,
  Menu as IconMenu,
  Location,
  Setting,
} from '@element-plus/icons-vue'
import { onMounted } from 'vue'
import { useFetch } from '@vueuse/core'

onMounted(async()=> {
  const { data }  = await useFetch(
    'https://api.stlouisfed.org/fred/category?category_id=10&api_key=040734c7c172353e3248d5fd01746335&file_type=json',
    {
      onFetchError(res) {
        console.log('onFetchError():', res);
        ElMessage({
          type: 'warning',
          duration: 8000,
          message: res.error.stack
        })
        ElMessage.error(JSON.stringify(res.error.message))
      }
    }
  )
})
</script>