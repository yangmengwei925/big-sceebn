<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        运单监控<dv-decoration-1 style="width: 60px; height: 20px" />
      </div>
      <div class="d-flex jc-center">
        <dv-scroll-board :config="config" :style="{'width':dwidth+'px','height':dheight+'px'}"/>
      </div>
    </div>
  </div>
</template>

<script>
import chartsMixnis from "../mixins/mixins"
export default {
  data() {
    return {
      config: {
        header: ["车辆号", "起点", "终点", "货物名称", "当前状态"],
        data: [
          ["京A88880", "上海", "北京","煤炭","装货中"],
          ["京A88881", "上海", "北京","煤炭","装货中"],
          ["京A88882", "上海", "北京","煤炭","装货中"],
          ["京A88883", "上海", "北京","煤炭","装货中"],
          [
            '<span style="color:#e062ae;">京A88884</span>', 
            '<span style="color:#e062ae;">上海</span>', 
            '<span style="color:#e062ae;">北京</span>', 
            '<span style="color:#e062ae;">煤炭</span>', 
            '<span style="color:#e062ae;">装货中</span>', 
          ],
          ["京A88885", "上海", "北京","煤炭","装货中"],
          ["京A88886", "上海", "北京","煤炭","装货中"],
          ["京A88887", "上海", "北京","煤炭","装货中"],
          ["京A88888", "上海", "北京","煤炭","装货中"],
          ["京A88889", "上海", "北京","煤炭","装货中"],
        ],
        columnWidth: [84,60,60,70]
      },
    };
  },
    mixins:[chartsMixnis],
  props: {},
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>