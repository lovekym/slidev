<template>
    <div  ref="chart" style="height:100%;width: 100%;"></div>
  </template>
  
  <script>
  import * as echarts from 'echarts';
  
  export default {
    data() {
      return {
        chart: null,
        dates: ['8.2', '8.3', '8.4', '8.5', '8.6', '8.7', '8.8'],
        temps: [5, 10, 15, 20, 30, 40, 50],
      };
    },
    mounted() {
      window.addEventListener('resize', () => {
  this.chart.resize();
});
setTimeout(() => {
      this.chart = echarts.init(this.$refs.chart);
      this.chart.setOption({
        title: {
          text: '重庆市未来一周天气预报',
        },
        tooltip: {
          trigger: 'axis',
        },
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: this.dates,
        },
        yAxis: {
          type: 'value',
          axisLabel: {
            formatter: '{value} °C',
          },
        },
        series: [
          {
            data: this.temps,
            type: 'line',
            areaStyle: {}, // 开启区域填充
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
              offset: 0, color: 'orange'
            }, {
              offset: 1, color: 'red'
            }]),
          },
        ],
      })
      },0);
    },
    beforeDestroy() {
      if (this.chart) {
        this.chart.dispose();
      }
    },
  };
  </script>
  