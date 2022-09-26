<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        <div>七日增长趋势</div>
        <tabs :tabs="tabs" @change="tabChange"/>
      </div>
      <div class="d-flex jc-center">
        <Echart
          :options="options"
          id="chart2"
         :height="cHeight"
         :width="cWidth"
        ></Echart>
      </div>
    </div>
  </div>
</template>

<script>
import Echart from "@/common/echart";
import chartsMixnis from "../mixins/mixins"
import tabs from "../tabs/index.vue";
export default {
  data() {
    return {
      tabs: [
        { name: "货主", index: 0 },
        { name: "司机", index: 1 },
        { name: "车辆", index: 2 },
      ],
      options: {
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: ["12.1", "12.2", "12.3", "12.4", "12.5", "12.6", "12.7"],
        },
        grid: {
          top:10,
          x:30
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [1.6, 1.9, 1.8, 1.3, 1.6, 1.5, 1.4],
            type: "line",
            areaStyle: {},
            smooth: true
          },
        ],
      },
    };
  },
  components: {
    Echart,
    tabs
  },
  mixins:[chartsMixnis],
  props: {
    cdata: {
      type: Object,
      default: () => ({}),
    },
  },
  methods:{
    tabChange(item) {
      if(item.index==0){
        this.options.series[0].data = [1.6, 1.9, 1.8, 1.3, 1.6, 1.5, 1.4]
      }else if(item.index==1){
        this.options.series[0].data = [1.3,1.6, 1.5,1.9, 1.8,  1.6,  1.4]
      }else{
        this.options.series[0].data = [1.5,1.8,1.6, 1.9,  1.3, 1.6,  1.4]
      }
    },
  }
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>