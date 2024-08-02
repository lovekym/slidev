<template>
  <div class="slidev-layout grid image-x">
    <div class="my-auto flex">
      <div class="w-1/2 flex justify-center items-center p-8 max-h-md object-cover" :class="imageOrder">
        <!-- <div  class="rounded-2xl border-image object-cover" ref="chart" style="height:400px;width: 400px;"></div> -->
        <chongqing />
      </div>
      <div class="w-1/2 flex flex-col justify-center" :class="textAlignment">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts';
import chongqing from '../components/g6.vue'
export default {
  components: {
    chongqing
  },
  props: {
    image: {
      type: String,
      required: true,
    },
    imageOrder: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      chart: null,
      dates: ['8.2', '8.3', '8.4', '8.5', '8.6', '8.7', '8.8'],
      temps: [5, 10, 15, 20, 30, 40, 50],
    };
  },
  computed: {
    imageOrderClass: function () {
      return this.imageOrder === 1 ? 'order-1' : 'order-2';
    }
  },
  mounted() {
    window.addEventListener('resize', () => {
      //this.chart.resize();
    });
    this.$nextTick(() => {
      // this.chart = echarts.init(this.$refs.chart);
      // this.chart.setOption({
      //   title: {
      //     text: '重庆市未来一周天气预报',
      //   },
      //   tooltip: {
      //     trigger: 'axis',
      //   },
      //   xAxis: {
      //     type: 'category',
      //     boundaryGap: false,
      //     data: this.dates,
      //   },
      //   yAxis: {
      //     type: 'value',
      //     axisLabel: {
      //       formatter: '{value} °C',
      //     },
      //   },
      //   series: [
      //     {
      //       data: this.temps,
      //       type: 'line',
      //       areaStyle: {}, // 开启区域填充
      //       color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
      //         offset: 0, color: 'orange'
      //       }, {
      //         offset: 1, color: 'red'
      //       }]),
      //     },
      //   ],
      // })
    });
  },
  beforeDestroy() {
    if (this.chart) {
      // this.chart.dispose();
    }
  },
};
</script>