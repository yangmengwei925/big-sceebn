<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        <div>司机排名</div>
        <tabs :tabs="tabs" @change="tabChange" />
      </div>
      <div class="d-flex jc-center">
        <div class="car_box">
          <div class="img_car">
            <img src="@/assets/drive.png" alt="" />
          </div>
          <div :class="`list${index}`" v-for="(item, index) in list" :key="index">
            <dv-border-box-13>
              <div class="list_box">
                {{ item.name }} {{ item.value }}
              </div>
            </dv-border-box-13>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import chartsMixnis from "../mixins/mixins";
import tabs from "../tabs/index.vue";
export default {
  data() {
    return {
      tabs: [
        { name: "发运量", index: 0 },
        { name: "发运车次", index: 1 },
        { name: "运费收入", index: 2 },
      ],
      list: [
        {
          name: "京A88881",
          value: 5500,
        },
        {
          name: "京A88882",
          value: 5300,
        },
        {
          name: "京A88883",
          value: 5100,
        },
        {
          name: "京A88884",
          value: 5200,
        },
        {
          name: "京A88885",
          value: 5800,
        },
      ],
    };
  },
  components: {
    tabs,
  },
  props: {},
  mixins: [chartsMixnis],
  methods: {
    tabChange(item) {
      if (item.index == 0) {
        this.list.forEach((item)=>{
          item.name = '苏A88888'
          item.value = 3000
        })
      } else if (item.index == 1) {
        this.list.forEach((item)=>{
          item.name = '沪A88888'
          item.value = 4000
        })
      } else {
        this.list.forEach((item)=>{
          item.name = '陕A88888'
          item.value = 5000
        })
      }
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../style/chartBoxStyle.scss";
.car_box {
  position: relative;
  width: 100%;
  height: 330px;
  .img_car {
    position: absolute;
    top: 60px;
    left: 0;
    img {
      width: 160px;
      height: 160px;
    }
  }
  .list0,
  .list1,
  .list2,
  .list3,
  .list4{
   
     position: absolute;
    top: 10px;
    left: 120px;
    width: 200px;
    height: 50px;
  }
  .list1{
    top: 80px;
    left: 140px;
  }
  .list2{
    top: 150px;
    left: 160px;
  }
  .list3{
    top: 220px;
    left: 140px;
  }
  .list4{
    top: 290px;
    left: 120px;
  }
  .list_box{
     display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
}
</style>