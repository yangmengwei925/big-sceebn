<template>
  <div id="normal_box">
    <div class="bg-color-black">
      <div class="title">
        统计分析<dv-decoration-1 style="width: 60px; height: 20px" />
      </div>
      <div class="d-flex jc-center">
        <dv-border-box-8 style="width: 520px">
          <div class="left">
            <div class="left_item" v-for="(item, index) in date1" :key="index">
              <div class="left_title">{{ item.name }}</div>
              <div class="left_num">{{ item.value }}单</div>
            </div>
          </div>
        </dv-border-box-8>

        <div class="right">
          <div class="right_item" v-for="(item, index) in date2" :key="index">
            <dv-border-box-8>
              <div class="right_box">
                <div class="right_title">{{ item.name }}</div>
                <div class="right_num">{{ item.value }}家</div>
              </div>
            </dv-border-box-8>
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
    return {
      date1: [
        {
          name: "今日运单量",
          value: 1000,
        },
        {
          name: "今日运单量",
          value: 1000,
        },
        {
          name: "今日运单量",
          value: 1000,
        },
        {
          name: "今日运单量",
          value: 1000,
        },
        {
          name: "今日运单量",
          value: 1000,
        },
        {
          name: "今日运单量",
          value: 1000,
        },
      ],
      date2: [
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
        {
          name: "累计货主",
          value: 1000,
        },
      ],
    };
  },

  props: {},
  mixins: [chartsMixnis],
};
</script>
<style lang="scss" scoped>
$box-width: 1190px;
$box-height: 410px;

#normal_box {
  padding: 16px;
  height: $box-height;
  width: $box-width;
  border-radius: 10px;
  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
    .title {
      display: flex;
      height: 50px;
      padding: 10px 0;
    }
    .left {
      width: 500px;
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      .left_item {
        width: 50%;
        height: 110px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        .left_title {
          font-size: 20px;
        }
        .left_num {
          font-size: 20px;
          color: rgb(255, 219, 92);
        }
      }
    }
    .right {
      width: 60%;
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;

      .right_item {
        .right_box {
          width: 140px;
          height: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
        }
        .right_title {
          font-size: 20px;
          margin-bottom: 30px;
        }
        .right_num {
          font-size: 20px;
          color: rgb(255, 219, 92);
        }
      }
    }
  }
}
</style>