<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        货物比例<dv-decoration-1 style="width: 60px; height: 20px" />
      </div>
      <div class="d-flex jc-center">
        <Echart
          :options="options"
          id="centreLeft1Chart"
          height="308px"
          width="364px"
        ></Echart>
      </div>
    </div>
  </div>
</template>

<script>
import Echart from "@/common/echart";
import chartsMixnis from "../mixins/mixins"
export default {
  data() {
    return {
      options: {
        color: [
          "#9fe6b8",
          "#ffdb5c",
          "#ff9f7f",
          "#fb7293",
          "#e7bcf3",
          "#8378ea",
          "#37a2da",
          "#32c5e9",
        ],
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b} : {c} ({d}%)",
        },
        toolbox: {
          show: true,
        },
        calculable: true,
        legend: {
          orient: "horizontal",
          icon: "circle",
          bottom: 0,
          x: "center",
          textStyle: {
            color: "#fff",
          },
        },
        series: [
          {
            name: "通过率统计",
            type: "pie",
            radius: [20, 80],
            roseType: "area",
            center: ["50%", "40%"],
            data: [
              { value: 20, name: "钢铁" },
              { value: 40, name: "煤炭" },
              { value: 40, name: "焦炭" },
            ],
            labelLine:{
                length:10,
                length2:10
            }
          },
        ],
      },
    };
  },
    mixins:[chartsMixnis],
  components: {
    Echart,
  },
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>