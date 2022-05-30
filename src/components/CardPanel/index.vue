<template>
  <div class="card-panel-container">
    <div v-if="cardType === 1" class="no-icon-card-panel" :style="{'--sub-content-bg-color':bgColor}">
      <div class="content">
        <div class="title">{{ serviceData.title || "未知" }}</div>
        <div class="label-wrapper">
          <div v-for="(item, index) in serviceData.dataList" :key="index" class="label">
            <span class="amount">{{ item.value || 0 }}</span>
            <span class="time">{{ item.time || '未知' }}</span>
          </div>
        </div>
      </div>
    </div>
    <div v-else-if="cardType === 2" class="color-green">cardType = 2</div>
  </div>
</template>

<script>
export default {
  props: {
    // 1，不带svg-icon；2，带svg-icon
    cardType: {
      type: Number,
      default: 1
    },
    serviceData: {
      type: Object,
      default: () => {}
    }
  },
  computed: {
    bgColor() {
      switch (this.serviceData.serviceType) {
        case 1:
          // 蓝色
          return '#1491FC'
        case 2:
          // 绿色
          return '#48D794'
        case 3:
          // 粉色
          return '#D479E6'
        default:
          return '#1491FC'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$font-color: #17242E;
$sub-content-bg-color: var(--sub-content-bg-color);

.card-panel-container {
  width: 100%;
  height: 100%;

  .no-icon-card-panel {
    width: inherit;
    height: inherit;

    .content {
      position: relative;
      height: inherit;
      padding: 10px 15px;
      box-sizing: border-box;

      &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 6px;
        height: inherit;
        background-color: $sub-content-bg-color;
      }

      .title {
        font-size: 14px;
        font-family: MicrosoftYaHei-Bold, MicrosoftYaHei;
        font-weight: bold;
        color: $font-color;
        line-height: 19px;
      }

      .label-wrapper {
        display: flex;
        justify-content: space-around;
        margin-top: 30px;
        width: inherit;

        .label {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          align-items: center;
          height: 62px;

          .amount {
            font-size: 26px;
            font-family: MicrosoftYaHei;
            color: $font-color;
            line-height: 35px;
          }

          .time {
            font-size: 14px;
            font-family: MicrosoftYaHei;
            color: $font-color;
            line-height: 19px;
          }
        }
      }
    }

  }
}
</style>
