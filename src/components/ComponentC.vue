<template>
  <div class="widget-content">
    <p>Content of Component C</p>
    <div id="chart">
      <apexchart type="line" height="200" :options="chartOptions" :series="series"></apexchart>
    </div>
  </div>
</template>

<script>
import VueApexCharts from 'vue3-apexcharts'

export default {
  name: 'ComponentC',
  components: {
    apexchart: VueApexCharts,
  },
  mounted() {
    var options = {
      chart: {
        type: 'bar'
      },
      series: [{
        name: 'sales',
        data: [30,40,45,50,49,60,70,91,125]
      }],
      xaxis: {
        categories: [1991,1992,1993,1994,1995,1996,1997, 1998,1999]
      }
    }

    var chart = new ApexCharts(document.querySelector("#chart"), options);

    chart.render();
  }
}
</script>

<style scoped>
.widget-content {
  padding: 20px;
  text-align: center;
}
</style>