<template>
  <el-table :data="tableData" style="font-size: medium" stripe border highlight-current-row>
    <el-table-column prop="goodsName" label="货品名称" width="180" />
    <el-table-column prop="price" label="单价" width="180" sortable/>
    <el-table-column prop="description" label="描述"/>
  </el-table>
  <button @click="handle()">clickHere</button>
</template>

<script setup>
import {reactive} from "vue";

const tableData=reactive([])

function handle(){
  tableData.push({
    goodsName: '苹果',
    price: 5,
    description: '好吃的苹果'
  })
}
</script>