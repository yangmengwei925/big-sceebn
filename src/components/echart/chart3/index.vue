<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        运价指数<dv-decoration-1 style="width: 60px; height: 20px" />
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
import chartsMixnis from "../mixins/mixins";
export default {
  data() {
    return {
      options: {
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: ["12.1", "12.2", "12.3", "12.4", "12.5", "12.6", "12.7"],
        },
        grid: {
          top: 10,
          x: 30,
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [1.6, 1.9, 1.8, 1.3, 1.6, 1.5, 1.4],
            type: "line",
            areaStyle: {},
            smooth: true,
			label: {
             show: true,
             position: 'top'
           },
          },
        ],
      },
    };
  },
  mixins: [chartsMixnis],
  components: {
    Echart,
  },
  props: {
    cdata: {
      type: Object,
      default: () => ({}),
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>