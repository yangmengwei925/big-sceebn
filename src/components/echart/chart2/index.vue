<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        各省发货量<dv-decoration-1 style="width: 60px; height: 20px" />
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
      options:{}
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
  created(){
    const cData = [
      {
      name:"江苏",
      value:59000
    },
    {
      name:"北京",
      value:49000
    },
    {
      name:"上海",
      value:39000
    },
    {
      name:"南京",
      value:29000,
      itemStyle: {
        color: 'red'
    }
    },
    ]
    this.setOptions(cData)
  },
  methods:{
    setOptions(data = []) {
            let [maxValue, temp] = [0, []]
            data.forEach((item) => {
                temp.push(item.value)
            })
            maxValue = Math.max.apply(null, temp)
            // 气泡颜色数组
            const color = ['#FAC858', '#FACD91', '#516CC0', '#EE6666', '#73C0DE', '#C280FF', '#91CC75', '#ff7123', '#ffc400', '#5e333f']
            // 气泡颜色备份
            let bakeColor = [...color]
            // 气泡数据
            const bubbleData = []
            // 气泡基础大小
            let basicSize = 70
            // 节点之间的斥力因子,值越大,气泡间距越大
            let repulsion = 380
            // 根据气泡数量配置基础大小和斥力因子（以实际情况进行适当调整，使气泡合理分布）
            if (data.length >= 5 && data.length < 10) {
                basicSize = 50
                repulsion = 230
            }
            if (data.length >= 10 && data.length < 20) {
                basicSize = 40
                repulsion = 150
            } else if (data.length >= 20) {
                basicSize = 30
                repulsion = 75
            }
            // 填充气泡数据数组bubbleData
            for (const item of data) {
                // 确保气泡数据条数少于或等于气泡颜色数组大小时，气泡颜色不重复
                if (!bakeColor.length) bakeColor = [...color]
                const colorSet = new Set(bakeColor)
                const curIndex = Math.round(Math.random() * (colorSet.size - 1))
                const curColor = bakeColor[curIndex]
                colorSet.delete(curColor)
                bakeColor = [...colorSet]
                // 气泡大小设置
                let size = (item.value * basicSize * 2) / maxValue
                if (size < basicSize) size = basicSize
                bubbleData.push({
                    name: item.name,
                    value: item.value,
                    symbolSize: size,
                    draggable: true,
                    itemStyle: {
                        normal: { 
                          color: curColor
                           },
                    },
                })
            }
            const bubbleOptions = {
                // backgroundColor: '#fff',
                animationEasingUpdate: 'bounceIn',
                series: [
                    {
                        type: 'graph',
                        layout: 'force',
                        force: {
                            repulsion: repulsion,
                            edgeLength: 10,
                        },
                        // 是否开启鼠标缩放和平移漫游
                        roam: false,
                        label: { 
                          normal: { 
                            show: true,
                            fontSize:20,
                            formatter:"{b}\n{c}"
                             } 
                          },
                        data: bubbleData,
                         animation:true,
                         symbol: "path://M512,512m-448,0a448,448,0,1,0,896,0a448,448,0,1,0,-896,0Z"
                    },
                ],
            }
            this.options = bubbleOptions
        }
  }
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
</style>