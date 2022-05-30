<template>
  <div class="app-container bg-color">
    <div class="doctor-table-area">
      <h4>待添加医生(123)</h4>
      <doctor-table />
    </div>
    <div style="margin-top:20px;">
      <el-row :gutter="20">
        <el-col :lg="8">
          <div class="grid-content">
            <card-panel :card-type="1" :service-data="orderData" />
          </div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content">
            <card-panel :card-type="1" :service-data="consultationeData" />
          </div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content">
            <card-panel :card-type="1" :service-data="transferData" />
          </div>
        </el-col>
      </el-row>
    </div>
    <div style="margin-top:20px;">
      <el-row :gutter="20">
        <el-col :lg="8">
          <div class="grid-content echart-height">
            <bar-chart />
          </div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content echart-height">预约转诊单</div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content echart-height">远程会诊单</div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import DoctorTable from './components/DoctorTable'
import CardPanel from '@/components/CardPanel'
import BarChart from './components/BarChart'

export default {
  name: 'Home',
  components: { DoctorTable, CardPanel, BarChart },
  data() {
    return {
      orderData: {
        title: '预约服务单近期数据',
        serviceType: 1,
        dataList: [
          {
            time: '今天',
            value: 347
          },
          {
            time: '一周',
            value: 666
          },
          {
            time: '一个月',
            value: 2657
          }
        ]
      },
      consultationeData: {
        title: '远程会诊近期数据',
        serviceType: 2,
        dataList: [
          {
            time: '今天',
            value: 82
          },
          {
            time: '一周',
            value: 260
          },
          {
            time: '一个月',
            value: 570
          }
        ]
      },
      transferData: {
        title: '转诊近期数据',
        serviceType: 3,
        dataList: [
          {
            time: '今天',
            value: 588
          },
          {
            time: '一周',
            value: 702
          },
          {
            time: '一个月',
            value: 3845
          }
        ]
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.doctor-table-area {
  padding: 20px;
  border-radius: 4px;
  width: inherit;
  background-color: #fff;
}

.grid-content {
  border-radius: 4px;
  height: 155px;
  background: #fff;
  overflow: hidden;
}

.echart-height {
  height: 380px;
}

@media (max-width: 1200px) {
  .grid-content {
    margin-bottom: 10px;
  }
}

</style>
