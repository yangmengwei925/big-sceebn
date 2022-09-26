<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        线路运距占比<dv-decoration-1 style="width: 60px; height: 20px" />
      </div>
      <div class="d-flex jc-center">
        <dv-capsule-chart
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
            name: "150-200",
            value: 10,
          },
          {
            name: "100-150",
            value: 30,
          },
          {
            name: "50-100",
            value: 20,
          },
          {
            name: "20-50",
            value: 15,
          },
          {
            name: "0-20",
            value: 5,
          },
        ],
        colors: ["#e062ae", "#fb7293", "#e690d1", "#32c5e9", "#96bfff"],
        unit: "%",
        showValue: true,
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