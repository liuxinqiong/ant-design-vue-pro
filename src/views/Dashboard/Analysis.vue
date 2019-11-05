<template>
  <div>
    <Charts :option="chartOption" style="height: 400px;"></Charts>
  </div>
</template>

<script>
import Charts from "../../components/Charts";
import request from "../../utils/request.js";
export default {
  components: {
    Charts
  },
  data() {
    return {
      chartOption: {}
    };
  },
  mounted() {
    this.getChartData();
  },
  methods: {
    getChartData() {
      request({
        url: "/api/dashboard/chart",
        method: "get",
        params: {
          ID: 12345
        }
      }).then(response => {
        this.chartOption = {
          title: {
            text: "123"
          },
          tooltip: {},
          xAxis: {
            data: ["1", "2", "3", "4", "5", "6"]
          },
          yAxis: {},
          series: [
            {
              name: "111",
              type: "bar",
              data: response.data
            }
          ]
        };
      });
    }
  }
};
</script>

<style></style>
