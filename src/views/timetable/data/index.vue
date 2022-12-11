<script setup>
import {
  Search,
  RefreshLeft,
  Clock,
  Refresh,
  Operation,
} from "@element-plus/icons-vue";
import { computed, ref } from "vue";
import data from "./data.json";
//计算表格高度
const { proxy } = getCurrentInstance();
let tableHeight = proxy.getInitTableHeight(-5);
//搜索数据
const name = ref("");
//假数据
const tableDataAll = computed(() => {
  return Array(100)
  .fill(data[0], 0, 100)
  .map((item,key)=>(
    {
      ...item,
      key:key+1
    }
  ))
});
//分页
const currentPage = ref(1);
const pageSize = ref(10);
const tableDataPage = computed(() => {
  return tableDataAll.value.slice((currentPage.value-1)*pageSize.value,currentPage.value*pageSize.value)
});
</script>
<template>
  <div class="app-container">
    <h4 class="app-title">数据列表</h4>
    <el-container>
      <el-header style="padding: 0;" class="el-header">
        <el-form :inline="true">
          <el-form-item label="教师/学生姓名">
            <el-input v-model="name" placeholder="教师/学生姓名"/>
          </el-form-item>
          <el-form-item label="课程编号/名称">
            <el-input placeholder="课程编号/名称"></el-input>
          </el-form-item>
        </el-form>
        <el-row class="el-header-buttons">
          <el-button type="info" :icon="RefreshLeft" class="grayBut">重置</el-button>
           <el-button type="primary" :icon="Search" class="blueBut">查询</el-button>
        </el-row>
      </el-header>
      <el-main style="padding: 0" class="el-main">
        <div class="tableButs">
          <el-button type="primary" :icon="Clock" class="blueBut">同步课程数据</el-button>
          <el-button :icon="Refresh" >刷新</el-button>
          <el-button :icon="Operation" >配置</el-button>
        </div>
        <el-table
          :height="tableHeight"
          :data="tableDataPage"
          style="width: 100%"
          stripe
        >
          <el-table-column type="selection" width="55" />
          <el-table-column prop="key" label="序号" width="50" align="center" />
          <el-table-column prop="id" label="ID" align="center" />
          <el-table-column prop="kcbh" label="课程编号" align="center"/>
          <el-table-column prop="kcmc" label="课程名称" align="center"/>
          <el-table-column prop="jsmc" label="教师名称" align="center"/>
          <el-table-column prop="jsgh" label="教师工号" align="center"/>
          <el-table-column prop="skrq" label="上课日期" sortable align="center"/>
          <el-table-column prop="kckssj" label="课程开始时间" sortable align="center"/>
          <el-table-column prop="kcjssj" label="课程结束时间" align="center"/>
          <el-table-column prop="tb" label="同步" align="center" width="100" />
          <el-table-column prop="tbsj" label="同步时间" align="center"/>
        </el-table>
      </el-main>
      <el-footer style="padding: 0" class="el-footer">
        <el-pagination
          v-model:current-page="currentPage"
          v-model:page-size="pageSize"
          :small="true"
          :background="true"
          layout="total,prev, pager,next, sizes"
          :total="tableDataAll.length"
        />
      </el-footer>
    </el-container>
  </div>
</template>

<style>
.app-title {
  font-weight: 600;
  margin-top: 5px;
}
.el-main {
  border-top: 1px solid rgb(241, 241, 241);
}
.grayBut {
  border: none;
  background-color: rgba(242, 243, 247);
  color: rgba(0, 0, 0, 0.4);
}
.tableButs {
  display: flex;
  justify-content: end;
  margin-top: 15px;
  margin-bottom: 5px;
}
.el-footer{
  display: flex;
  justify-content: end;
}
.el-header{
  display: flex;
  height:auto;
}
.el-header-buttons{
  display: flex;
  flex-grow: 1;
  justify-content: flex-end;
}
.blueBut{
  background-color: rgb(39, 102, 255);
}
</style>