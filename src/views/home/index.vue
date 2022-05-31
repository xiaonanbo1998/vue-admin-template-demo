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
            <card-panel :card-type="1" :service-data="consultationData" />
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
            <bar-chart :option-data="orderEchartsData" />
            <span class="link">查看详情</span>
          </div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content echart-height">
            <bar-chart :option-data="consultationEchartsData" />
            <span class="link">查看详情</span>
          </div>
        </el-col>
        <el-col :lg="8">
          <div class="grid-content echart-height">
            <bar-chart :option-data="transferEchartsData" />
            <span class="link">查看详情</span>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import { orderData, consultationData, transferData } from './CardPanelData.json'
import EchartsData from './EchartsData.json'

import DoctorTable from './components/DoctorTable'
import CardPanel from '@/components/CardPanel'
import BarChart from './components/BarChart'

export default {
  name: 'Home',
  components: { DoctorTable, CardPanel, BarChart },
  data() {
    return {
      ...{ orderData, consultationData, transferData }
    }
  },
  computed: {
    orderEchartsData: () => EchartsData.serviceData,
    consultationEchartsData: () => EchartsData.consultationData,
    transferEchartsData: () => EchartsData.transferData
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
  transition: all 0.5s;

  &:hover {
    box-shadow: 0px 10px 24px 0px rgba(9, 94, 166, 0.3);
    transform: translateY(-3px);
  }
}

.echart-height {
  position: relative;
  height: 380px;

  .link {
    position: absolute;
    top: 12px;
    right: 26px;
    font-size: 14px;
    font-family: MicrosoftYaHei;
    color: #9B9B9B;
    line-height: 19px;
    cursor: pointer;

    &::after {
      content: '>';
      margin-left: 5px;
      color: #9B9B9B;
      line-height: 19px;
      cursor: pointer;
    }
  }
}

@media (max-width: 1200px) {
  .grid-content {
    margin-bottom: 10px;
  }
}

</style>
