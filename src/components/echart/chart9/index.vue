<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        统计指标<dv-decoration-1 style="width: 60px; height: 20px" />
      </div>
      <div class="d-flex jc-center">
        <div class="content">
          <div class="line_box">
              <dv-border-box-13 class="z_box">
                  <div class="text_box">装货中:10</div>
              </dv-border-box-13>
            <dv-border-box-13 class="z_box">
                  <div class="text_box">运输中:10</div>
              </dv-border-box-13>
          </div>
          <div class="line_box1">
              <dv-border-box-13 class="z_box">
                  <div class="text_box">装货中:10</div>
              </dv-border-box-13>
            <dv-border-box-13 class="z_box">
                  <div class="text_box">运输中:10</div>
              </dv-border-box-13>
          </div>
          <div class="line_box">
              <dv-border-box-13 class="z_box">
                  <div class="text_box">装货中:10</div>
              </dv-border-box-13>
            <dv-border-box-13 class="z_box">
                  <div class="text_box">运输中:10</div>
              </dv-border-box-13>
          </div>
          <div class="line_box1">
              <dv-border-box-13 class="z_box">
                  <div class="text_box">装货中:10</div>
              </dv-border-box-13>
            <dv-border-box-13 class="z_box">
                  <div class="text_box">运输中:10</div>
              </dv-border-box-13>
          </div>
          <div class="line_box">
              <dv-border-box-13 class="z_box">
                  <div class="text_box">装货中:10</div>
              </dv-border-box-13>
            <dv-border-box-13 class="z_box">
                  <div class="text_box">运输中:10</div>
              </dv-border-box-13>
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import chartsMixnis from "../mixins/mixins";
export default {
  data() {
    return {};
  },

  props: {},
  mixins: [chartsMixnis],
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
.content{
     width: 100%;
    .line_box,
    .line_box1{
        display: flex;
        width: 100%;
        justify-content: flex-end;
        .z_box{
            display: flex;
            justify-content: space-around;
            align-items: center;
            width: 160px;
            height: 50px;
            margin-top: 10px;
            .text_box{
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100%;
            }
        }
    }
    .line_box1{
        justify-content: flex-start;
    }
}
</style>