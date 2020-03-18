<script>
  import {
    onMount,
    afterUpdate
  } from 'svelte';

  $: labels = [];
  $: values = [];
  export let data;
  var myChart;
  var ctx;

  function createChart() {

    console.log(data, 'currentadat')
    ctx = document.getElementById('myChart').getContext('2d');
    if (myChart) {
      myChart.destroy();
    };
    prepareData();
    myChart = new Chart(ctx, {
      type: 'horizontalBar',
      data: {
        labels,
        datasets: [{
          // label: 'Affected Population',
          data: values,
          backgroundColor: [
            'rgba(255, 99, 132, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(75, 192, 192, 0.2)',
            'rgba(153, 102, 255, 0.2)',
            'rgba(255, 159, 64, 0.2)'
          ],
          borderColor: [
            'rgba(255, 99, 132, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(75, 192, 192, 1)',
            'rgba(153, 102, 255, 1)',
            'rgba(255, 159, 64, 1)'
          ],
          borderWidth: 1
        }]
      },
      options: {
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true
            }
          }]
        }
      }
    });
  };

  function prepareData() {
    if (data.length > 0) {
      for (let i = 0; i < 5; i++) {

        labels.push(data[i]['country']);
        values.push(data[i]['cases']);
      }
      let india = data.filter(o => o.country === 'India');
      let obj = {};
      labels.push(india[0]['country']);
      values.push(india[0]['cases']);
      labels = labels;
      values = values;
    }
  }

  afterUpdate(createChart)
</script>

<div class="my-canvas">
  <canvas id="myChart"
  width="2"
  height="1">
</canvas>
</div>

<style>
.my-canvas {
  height: 80%;
  width: 80%;
}
</style>