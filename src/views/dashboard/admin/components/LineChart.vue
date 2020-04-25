<template>
  <div :class="className" :style="{height:height,width:width}" />
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import resize from './mixins/resize'

export default {
  mixins: [resize],
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '350px'
    },
    autoResize: {
      type: Boolean,
      default: true
    },
    chartData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      chart: null
    }
  },
  watch: {
    chartData: {
      deep: true,
      handler(val) {
        this.setOptions(val)
      }
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.initChart()
    })
  },
  beforeDestroy() {
    if (!this.chart) {
      return
    }
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    initChart() {
      this.chart = echarts.init(this.$el, 'macarons')
      this.setOptions(this.chartData)
    },
    setOptions({ expectedData, actualData, guichiquData, shitaiData, dongzhiData, jiuhuashanData } = {}) {
      this.chart.setOption({
        xAxis: {
          data: ['8：00', '9：00', '10：00', '11：00', '12：00', '13：00', '14：00', '15：00', '16：00', '17：00', '18：00', '19：00', '20：00'],
          boundaryGap: false,
          axisTick: {
            show: false
          }
        },
        grid: {
          left: 10,
          right: 10,
          bottom: 20,
          top: 30,
          containLabel: true
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross'
          },
          padding: [5, 10]
        },
        yAxis: {
          axisTick: {
            show: false
          }
        },
        legend: {
          data: ['青阳', '贵池区', '石台', '东至', '九华山']
        },
        series: [
        {
          name: '青阳',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#9999fa',
              lineStyle: {
                color: '#9999fa',
                width: 2
              },
              areaStyle: {
                color: '#f3f8ff'
              }
            }
          },
          data: actualData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'
        }, {
          name: '贵池区',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#EE82EE',
              lineStyle: {
                color: '#EE82EE',
                width: 2
              },
              areaStyle: {
                color: '#f3f0ff'
              }
            }
          },
          data: guichiquData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'

        }, {
          name: '石台',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#088A29',
              lineStyle: {
                color: '#088A29',
                width: 2
              },
              areaStyle: {
                color: '#f3f1ff'
              }
            }
          },
          data: shitaiData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'

        }, {
          name: '东至',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#81F7F3',
              lineStyle: {
                color: '#81F7F3',
                width: 2
              },
              areaStyle: {
                color: '#f3f8fb'
              }
            }
          },
          data: dongzhiData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'

        }, {
          name: '九华山',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#2E2E2E',
              lineStyle: {
                color: '#2E2E2E',
                width: 2
              },
              areaStyle: {
                color: '#f3f8fa'
              }
            }
          },
          data: jiuhuashanData,
          animationDuration: 2800,
          animationEasing: 'quadraticOut'

        }]
      })
    }
  }
}
</script>
