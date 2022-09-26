<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        7日作业指标趋势图<dv-decoration-1 style="width: 60px; height: 20px" />
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
import mapDate from "./date";
import chinaDate from './china'
import chartsMixnis from "../mixins/mixins"
export default {
  data() {
    return {
      series: [],
      tooltip: {},
    };
  },
  components: {
    Echart,
  },
    mixins:[chartsMixnis],
  computed: {
    options() {
      var options = {
        // tooltip: {
        //   trigger: "item",
        //   backgroundColor: "rgba(166, 200, 76, 0.82)",
        //   borderColor: "#FFFFCC",
        //   showDelay: 0,
        //   hideDelay: 0,
        //   enterable: true,
        //   transitionDuration: 0,
        //   extraCssText: "z-index:100",
        //   formatter: function (params) {
        //     //根据业务自己拓展要显示的内容
        //     var res = "";
        //     var name = params.name;
        //     var value = params.value[params.seriesIndex + 1];
        //     res =
        //       "<span style='color:#fff;'>" +
        //       name +
        //       "</span><br/>数据：" +
        //       value;
        //     return res;
        //   },
        // },
        visualMap: {
          //图例值控制
          show: false,
        },
        geo: {
          map: "china",
          zoom: 1.2,
          label: {
            emphasis: {
              show: false,
            },
          },
          roam: true, //是否允许缩放
          itemStyle: {
            normal: {
              areaColor:"#1A5CD7",
              borderColor: "#516a89", //省市边界线00fcff 516a89
              borderWidth: 1,
            }
          },
        },
        series: this.series,
      };
      return options;
    },
  },
  props: {},
  mounted() {
    console.log("-----------");
    console.log(this.$echarts);
    chinaDate()
    this.getSeries();
  },
  methods: {
    getSeries() {
      //   let echarts = this.$echarts;
      var series = [];
      [["北京市", mapDate.chinaDatas]].forEach(function (item) {
        console.log(item);
        series.push(
          {
            type: "lines",
            zlevel: 2,
            effect: {
              show: true,
              period: 4, //箭头指向速度，值越小速度越快
              trailLength: 0.02, //特效尾迹长度[0,1]值越大，尾迹越长重
              symbol: "arrow", //箭头图标
              symbolSize: 5, //图标大小
            },
            lineStyle: {
              normal: {
                width: 1, //尾迹线条宽度
                opacity: 1, //尾迹线条透明度
                curveness: 0.3, //尾迹线条曲直度
              },
            },
            data: mapDate.convertData(item[1]),
          },
          {
            type: "effectScatter",
            coordinateSystem: "geo",
            zlevel: 2,
            rippleEffect: {
              //涟漪特效
              period: 4, //动画时间，值越小速度越快
              brushType: "stroke", //波纹绘制方式 stroke, fill
              scale: 4, //波纹圆环最大限制，值越大波纹越大
            },
            label: {
              normal: {
                show: true,
                position: "right", //显示位置
                offset: [5, 0], //偏移设置
                formatter: function (params) {
                  //圆环显示文字
                  return params.data.name;
                },
                fontSize: 13,
              },
              emphasis: {
                show: true,
              },
            },
            symbol: "circle",
            symbolSize: function (val) {
              return 5 + val[2] * 5; //圆环大小
            },
            // itemStyle: {
            //   normal: {
            //     show: false,
            //     color: "#f00",
            //   },
            // },
            data: item[1].map(function (dataItem) {
              return {
                //在这里定义你所要展示的数据
                name: dataItem[0].name,
                value: mapDate.geoCoordMap[dataItem[0].name].concat([
                  dataItem[0].value,
                ]),
              };
            }),
          },
          //中心点
          {
            type: "scatter",
            coordinateSystem: "geo",
            zlevel: 2,
            rippleEffect: {
              period: 4,
              brushType: "stroke",
              scale: 4,
            },
            label: {
              normal: {
                show: true,
                position: "right",
                //offset:[5, 0],
                // color: "#0f0",
                formatter: "{b}",
                // textStyle: {
                //   color: "#0f0",
                // },
              },
              emphasis: {
                show: true,
                color: "#f60",
              },
            },
            symbol: "pin",
            symbolSize: 50,
            data: [
              {
                name: item[0],
                value: mapDate.geoCoordMap[item[0]].concat([10]),
              },
            ],
          }
        );
      });
      this.series = series;
    },
  },
};
</script>
<style lang="scss" scoped>
@import '../style/chartBoxStyle.scss';
</style>