<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        <div>承运商排名TOP10</div>
       <tabs :tabs="tabs" @change="tabChange"/>
      </div>
      <div class="d-flex jc-center">
        <dv-scroll-ranking-board
          :config="config"
          :style="{'width':dwidth+'px','height':dheight+'px'}"
        />
      </div>
    </div>
  </div>
</template>

<script>
import chartsMixnis from "../mixins/mixins"
import tabs from "../tabs/index.vue";
export default {
  data() {
    return {
      tabs: [
        { name: "发运量", index: 0 },
        { name: "发运车次", index: 1 },
        { name: "运费收入", index: 2 },
      ],
      config: {
        data: [
            {
              name: "新加坡东方海皇集团",
              value: 5500,
            },
            {
              name: "香港东方海外公司",
              value: 5300,
            },
            {
              name: "UPS公司",
              value: 5100,
            },
            {
              name: "马士基集团",
              value: 5200,
            },
            {
              name: "中国远洋运输集团公司",
              value: 5800,
            },
            {
              name: "中国外运股份有限公司",
              value: 5900,
            },
            {
              name: "北京宅急送快运股份有限公司",
              value: 4300,
            },
            {
              name: "中集集团",
              value: 3300,
            },
            {
              name: "宝供物流企业集团",
              value: 2300,
            },
            {
              name: "英国英运物流集团",
              value: 2000,
            },
        ],
      },
    };
  },
  components:{
    tabs
  },
  mixins:[chartsMixnis],
  props: {},
  methods:{
     tabChange(item) {
      if(item.index==0){
        this.config.data[0].value = 5500
      }else if(item.index==1){
        this.config.data[0].value = 6500
      }else{
        this.config.data[0].value = 7500
      }
    },
  }
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>