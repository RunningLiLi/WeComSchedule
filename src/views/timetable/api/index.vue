<script setup>
import { computed, ref } from "vue";

</script>
<template>
  <div class="app-container">
    <h4 class="app-title">本科同步接口设置</h4>
    <el-container>
      <el-header style="padding: 0;" class="el-header">
      </el-header>
      <el-main style="padding: 0" class="el-main">
        
      </el-main>
      <el-footer style="padding: 0" class="el-footer">
       
      </el-footer>
    </el-container>
  </div>
</template>

<style>
.app-title {
  font-weight: 600;
  margin-top: 15px;
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