<template>
  <div id="index" ref="appRef">
    <div class="bg">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 class="dv-dec-10" />
          <div class="d-flex jc-center">
            <dv-decoration-8 class="dv-dec-8" :color="decorationColor" />
            <div class="title">
              <span class="title-text">智运无车承运人平台</span>
              <dv-decoration-6
                class="dv-dec-6"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
              />
            </div>
            <dv-decoration-8
              class="dv-dec-8"
              :reverse="true"
              :color="decorationColor"
            />
          </div>
          <dv-decoration-10 class="dv-dec-10-s" />
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex aside-width">
            <div class="react-left ml-4 react-l-s">
              <span class="react-left"></span>
              <span class="text"></span>
            </div>
            <div class="react-left ml-3">
              <span class="text"></span>
            </div>
          </div>
          <div class="d-flex aside-width">
            <div class="react-right bg-color-blue mr-3">
              <span class="text fw-b"></span>
            </div>
            <div class="react-right mr-4 react-l-s">
              <span class="react-after"></span>
              <span class="text"
                >{{ dateYear }} {{ dateWeek }} {{ dateDay }}</span
              >
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-12 class="chart1">
                <chart1 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart2 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart3 />
              </dv-border-box-12>
            </div>
            <div class="chart_map">
              <dv-border-box-12>
                <centerMap />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart4">
                <chart4 />
              </dv-border-box-12>
            </div>
            <!-- <div>
              <dv-border-box-12 class="chart5">
                <centerLeft1 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart6">
                <centerLeft1 />
              </dv-border-box-12>
            </div> -->
          </div>
          <!-- 第四行 -->
          <div class="content-box">
            <div>
              <dv-border-box-12 class="chart1">
                <chart6 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart7 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart8 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart4">
                <chart9 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart5">
                <chart10 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart6">
                <chart11 />
              </dv-border-box-12>
            </div>
          </div>
          <!-- 第五行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-12 class="chart1">
                <chart12 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart13 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart14 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart15 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart16 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart17 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart18 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12 class="chart1">
                <chart19 />
              </dv-border-box-12>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import drawMixin from "../utils/drawMixin";
import { formatTime } from "../utils/index.js";
// import centerLeft1 from "./centerLeft1";
import centerMap from "@/components/echart/centerMap/index";
import chart1 from "@/components/echart/chart1";
import chart2 from "@/components/echart/chart2";
import chart3 from "@/components/echart/chart3";
import chart4 from "@/components/echart/chart4";
import chart6 from "@/components/echart/chart6";
import chart7 from "@/components/echart/chart7";
import chart8 from "@/components/echart/chart8";
import chart9 from "@/components/echart/chart9";
import chart10 from "@/components/echart/chart10";
import chart11 from "@/components/echart/chart11";
import chart12 from "@/components/echart/chart12";
import chart13 from "@/components/echart/chart13";
import chart14 from "@/components/echart/chart14";
import chart15 from "@/components/echart/chart15";
import chart16 from "@/components/echart/chart16";
import chart17 from "@/components/echart/chart17";
import chart18 from "@/components/echart/chart18";
import chart19 from "@/components/echart/chart19";
// import centerLeft2 from './centerLeft2'
// import centerRight1 from './centerRight1'
// import centerRight2 from './centerRight2'
// import center from './center'
// import bottomLeft from './bottomLeft'
// import bottomRight from './bottomRight'

export default {
  mixins: [drawMixin],
  data() {
    return {
      timing: null,
      loading: true,
      dateDay: null,
      dateYear: null,
      dateWeek: null,
      weekday: ["周日", "周一", "周二", "周三", "周四", "周五", "周六"],
      decorationColor: ["#568aea", "#000000"],
    };
  },
  components: {
    // centerLeft1,
    chart1,
    centerMap,
    chart2,
    chart3,
    chart4,
    chart6,
    chart7,
    chart8,
    chart9,
    chart10,
    chart11,
    chart12,
    chart13,
    chart14,
    chart15,
    chart16,
    chart17,
    chart18,
    chart19
    // centerLeft2,
    // centerRight1,
    // centerRight2,
    // center,
    // bottomLeft,
    // bottomRight
  },
  mounted() {
    this.timeFn();
    this.cancelLoading();
  },
  beforeDestroy() {
    clearInterval(this.timing);
  },
  methods: {
    timeFn() {
      this.timing = setInterval(() => {
        this.dateDay = formatTime(new Date(), "HH: mm: ss");
        this.dateYear = formatTime(new Date(), "yyyy-MM-dd");
        this.dateWeek = this.weekday[new Date().getDay()];
      }, 1000);
    },
    cancelLoading() {
      setTimeout(() => {
        this.loading = false;
      }, 500);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/index.scss";
.chart1 {
  position: relative;
  top: 0;
  left: 0;
}
.chart2 {
  position: relative;
  top: 0;
  left: 0px;
}
.chart_map {
  position: absolute;
  top: 134px;
  left: 1203px;
}
.chart4,
.chart5,
.chart6 {
  position: relative;
  top: 0;
  left: 792px;
}
</style>
