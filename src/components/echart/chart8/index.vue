<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        <div>车型和发货量</div>
        <tabs :tabs="tabs" @change="tabChange"/>
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
import tabs from "../tabs/index.vue";
export default {
  data() {
    return {
        tabs: [
        { name: "车型占比", index: 0 },
        { name: "发运量占比", index: 1 }
      ],
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
            name: "车型和发货量",
            type: "pie",
            radius: [20, 80],
            roseType: "area",
            center: ["50%", "40%"],
            data: [
              { value: 20, name: "高栏车" },
              { value: 40, name: "牵引车" },
              { value: 50, name: "普通货车" },
              { value: 60, name: "危险品车" },
              { value: 70, name: "冷藏车" },
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
    tabs
  },
   methods: {
    tabChange(item) {
      if(item.index==0){
        this.options.series[0].data = [
          { value: 20, name: "高栏车" },
              { value: 40, name: "牵引车" },
              { value: 50, name: "普通货车" },
              { value: 60, name: "危险品车" },
              { value: 70, name: "冷藏车" },
        ]
      }else{
        this.options.series[0].data = [
          { value: 70, name: "高栏车" },
              { value: 60, name: "牵引车" },
              { value: 50, name: "普通货车" },
              { value: 40, name: "危险品车" },
              { value: 20, name: "冷藏车" },
         ]
      }
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>