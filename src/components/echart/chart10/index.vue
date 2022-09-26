<template>
  <div id="normal_box">
    <div class="bg-color-black">
        <div class="title">
          <div>7日作业指标趋势图</div>    
          <tabs :tabs="tabs" @change="tabChange"/>
        </div>
      <div class="d-flex jc-center">
    <Echart
      :options="options"
      id="lineChart1"
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
        { name: "运单量", index: 0 },
        { name: "发运量", index: 1 },
        { name: "发运车次", index: 2 },
      ],
      options: {
        xAxis: {
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: "bar",
          },
        ],
        grid:{
            top:10
        }
      },
    };
  },
   mixins:[chartsMixnis],
  components: {
    Echart,
    tabs
  },
  props: {
    cdata: {
      type: Object,
      default: () => ({}),
    },
  },
   methods: {
    tabChange(item) {
      if(item.index==0){
        this.options.series[0].data = [120, 200, 150, 80, 70, 110, 130]
      }else if(item.index==1){
        this.options.series[0].data = [200,120,150, 130,  110, 80, 70  ]
      }else{
        this.options.series[0].data = [110,120,130,  150, 80, 70, 200 ]
      }
    },
  },
};
</script>
<style lang="scss" scoped>
@import '../style/chartBoxStyle.scss';
</style>