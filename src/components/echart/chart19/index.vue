<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
       热门线路运次排名<dv-decoration-1 style="width: 60px; height: 20px" />
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
export default {
  data() {
    return {
      config: {
        data: [
          
            {
              name: "北京---上海",
              value: 5500,
            },
            {
              name: "北京---上海",
              value: 5300,
            },
            {
              name: "北京---上海",
              value: 5100,
            },
            {
              name: "北京---上海",
              value: 5200,
            },
            {
              name: "北京---上海",
              value: 5800,
            },
            {
              name: "北京---上海",
              value: 5900,
            },
            {
              name: "北京---上海",
              value: 4300,
            },
            {
              name: "北京---上海",
              value: 3300,
            },
            {
              name: "北京---上海",
              value: 2300,
            },
            {
              name: "北京---上海",
              value: 2000,
            },
        ],
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