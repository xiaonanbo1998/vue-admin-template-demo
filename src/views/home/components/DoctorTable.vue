<template>
  <div class="doctor-table-container">
    <el-table :data="tableData" fit stripe style="width: 100%" :header-cell-style="{ background: '#F0F0F0', color: '#000000' }">
      <el-table-column prop="name" label="医生姓名" align="center" />
      <el-table-column prop="gender" label="性别">
        <template slot-scope="scope">
          {{ scope.row.gender === 0 ? '男' : '女' }}
        </template>
      </el-table-column>
      <el-table-column prop="title" label="职称" />
      <el-table-column prop="hospital" label="医院" />
      <el-table-column prop="department" label="科室" />
      <el-table-column label="操作">
        <span class="detail">查看详情</span>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import doctorData from '../doctorData.json'

export default {
  data() {
    return {
    }
  },
  computed: {
    tableData() {
      return doctorData.list
    }
  }
}
</script>

<style scoped>
.detail {
  color: #1491FC;
  cursor: pointer;
}
</style>
