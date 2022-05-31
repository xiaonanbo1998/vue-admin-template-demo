<template>
  <div ref="barChart" class="bar-chart-container" />
</template>

<script>
import * as echarts from 'echarts'
import { debounce } from '@/utils'

export default {
  props: {
    optionData: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      // 重绘函数
      resizeHandler: null,
      myChart: null,
      defaultOption: {
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
        grid: {
          top: 80,
          bottom: 20
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
            label: {
              show: true,
              position: 'top',
              fontSize: 14,
              fontFamily: 'MicrosoftYaHei',
              color: '#9b9b9b'
            },
            itemStyle: {
              color: '#A0C8F7',
              borderRadius: [50, 50, 0, 0]
            }
          }
        ]
      }
    }
  },
  mounted() {
    // 添加防抖，定义回调
    this.resizeHandler = debounce(() => {
      if (this.myChart) {
        this.myChart.resize()
      }
    }, 100)
    // 添加监听
    this.initResizeEvent()

    this.$nextTick(() => {
      this.initChart()
    })
  },
  beforeDestroy() {
    this.destroyResizeEvent()
  },
  // to fixed bug when cached by keep-alive
  // https://github.com/PanJiaChen/vue-element-admin/issues/2116
  activated() {
    this.$_initResizeEvent()
    this.$_initSidebarResizeEvent()
  },
  deactivated() {
    this.$_destroyResizeEvent()
    this.$_destroySidebarResizeEvent()
  },
  methods: {
    initChart() {
      this.myChart = echarts.init(this.$refs.barChart)

      const option = Object.assign({}, this.defaultOption)
      // 标题
      option.title.text = this.optionData.title
      // 副标题，数量
      option.title.subtext = this.optionData.subtext
      // 月数据
      option.series[0].data = JSON.parse(JSON.stringify(this.optionData.data))
      // 柱形条颜色
      option.series[0].itemStyle.color = this.optionData.color

      this.myChart.setOption(option)
    },
    initResizeEvent() {
      window.addEventListener('resize', this.resizeHandler)
    },
    destroyResizeEvent() {
      window.removeEventListener('resize', this.resizeHandler)
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
