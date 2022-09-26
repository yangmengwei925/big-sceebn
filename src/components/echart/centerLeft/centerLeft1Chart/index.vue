<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue';
export default {
  data () {
    return {
      cdata: {
        xData: ["钢铁", "煤炭", "焦炭", "data4", "data5", "data6"],
        seriesData: [
          { value: 20, name: "钢铁" },
          { value: 40, name: "煤炭" },
          { value: 40, name: "焦炭" }
        ]
      }
    }
  },
  components: {
    Chart,
  },
  mounted () {
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
</style>