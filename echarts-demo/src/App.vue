<template>
  <div id="app">
    <e-charts class="chart" :option="option"></e-charts>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      data: this.getRandomDate(),
    };
  },
  computed: {
    option() {
      return {
        xAxis: {
          type: "category",
          // 数组映射
          data: this.data.map((d) => d.time),
        },
        yAxis: { type: "value" },
        series: [
          {
            name: "销量",
            type: "line",
            data: this.data.map((d) => d.value),
          },
        ],
      };
    },
  },
  methods: {
    getRandomDate() {
      return [
        {
          time: "2023-01-30",
          value: Math.random() * 100,
        },
        {
          time: "2023-01-30",
          value: Math.random() * 100,
        },
        {
          time: "2023-01-30",
          value: Math.random() * 100,
        },
        {
          time: "2023-01-30",
          value: Math.random() * 100,
        },
      ]; //return 后面应该是分号
    },
  },
  created() {
    setInterval(() => {
      this.data = this.getRandomDate();
    }, 1000);
  },
};
</script>

<style lang="css" scoped>
.chart {
  height: 400px;
}
</style>
