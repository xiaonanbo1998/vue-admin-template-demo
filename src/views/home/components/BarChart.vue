<template>
  <div ref="barChart" class="bar-chart-container" />
</template>

<script>
import * as echarts from 'echarts'

export default {
  mounted() {
    this.$nextTick(() => {
      this.initChart()
    })
  },
  methods: {
    initChart() {
      var myChart = echarts.init(this.$refs.barChart)

      var option = {
        title: {
          text: '预约服务单',
          subtext: '2657',
          subtextStyle: {
            fontSize: 22,
            fontFamily: 'MicrosoftYaHei',
            color: '#17242e',
            lineHeight: 30
          }
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow'
          }
        },
        xAxis: {
          type: 'category',
          data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月']
        },
        yAxis: {
          type: 'value',
          axisLine: {
            show: true,
            symbol: ['none', 'arrow']
          },
          splitLine: {
            lineStyle: {
              width: 2,
              type: 'dashed'
            }
          }
        },
        series: [
          {
            name: '增长率',
            data: [6, 5, 9, 7, 8, 13, 17, 25, 18, 17, 18, 11],
            type: 'bar',
            itemStyle: {
              color: '#A0C8F7',
              borderRadius: [50, 50, 0, 0]
            }
          }
        ]
      }

      myChart.setOption(option)
    }
  }
}
</script>

<style lang="scss" scoped>
.bar-chart-container {
  padding: 10px 15px;
  width: inherit;
  height: inherit;
  box-sizing: border-box;
}
</style>
