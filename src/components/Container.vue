<template>
      <el-container class="h-full">
        <el-header>Header</el-header>
        <el-container>
          <el-aside width="250px">
            <Sidebar />
            
          </el-aside>
          <el-container>
            <el-main>Main</el-main>
            <el-footer>Footer</el-footer>
          </el-container>
        </el-container>
      </el-container>
</template>
  
<script setup>
import Sidebar from '@/components/Sidebar.vue'
</script>