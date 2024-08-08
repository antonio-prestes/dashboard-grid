<template>
  <div class="widget-content">
    <p>Content of Component B</p>
    <div style="width: 800px;"><canvas id="acquisitions1"></canvas></div>
  </div>
</template>

<script>
import Chart from 'chart.js/auto'
export default {
  name: 'ComponentB',
  mounted() {
    (async function() {
      const data = [
        { year: 2010, count: 10 },
        { year: 2011, count: 20 },
        { year: 2012, count: 15 },
        { year: 2013, count: 25 },
        { year: 2014, count: 22 },
        { year: 2015, count: 30 },
        { year: 2016, count: 28 },
      ];

      new Chart(
        document.getElementById('acquisitions1'),
        {
          type: 'line',
          data: {
            labels: data.map(row => row.year),
            datasets: [
              {
                label: 'Acquisitions by year',
                data: data.map(row => row.count)
              }
            ]
          }
        }
      );
    })();
  }
}
</script>

<style scoped>
.widget-content {
  padding: 20px;
  text-align: center;
}
</style>