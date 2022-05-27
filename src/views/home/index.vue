<template>
  <div class="app-container bg-color">
    <div class="doctor-table-area">
      <h4>待添加医生(123)</h4>
      <doctor-table />
    </div>
    <div style="margin-top:20px;">
      按时间统计数据
    </div>
    <div style="margin-top:20px;">
      条形统计图
    </div>
  </div>
</template>

<script>
import DoctorTable from './components/DoctorTable'

export default {
  name: 'Home',
  components: { DoctorTable }
}
</script>

<style lang="scss" scoped>
.doctor-table-area {
  padding: 20px;
  border-radius: 4px;
  width: inherit;
  background-color: #fff;
}
</style>
