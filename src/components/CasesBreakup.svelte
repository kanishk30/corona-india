<script>
    import {
      onMount,
      afterUpdate
    } from 'svelte';

    $: labels = [];
    $: values = [];
    $: cases = 0;
    $: todayCases = 0;
    $: deaths = 0;
    $: todayDeaths = 0;
    $: recovered = 0;
    $: active = 0;
    $: critical = 0;

    export let data = [];
    var myChart;
    var ctx;

    function createChart() {
      ctx = document.getElementById('breakdown').getContext('2d');
      if (myChart) {
        myChart.destroy();
      };
      prepareData();
      myChart = new Chart(ctx, {
        type: 'doughnut',
        data: {
          labels,
          datasets: [{
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
        cases = data.reduce((a, b) => ({cases: a.cases + b.cases})).cases; // returns object
        todayCases = data.reduce((a, b) => ({todayCases: a.todayCases + b.todayCases})).todayCases;
        deaths = data.reduce((a, b) => ({deaths: a.deaths + b.deaths})).deaths; // returns object
        todayDeaths = data.reduce((a, b) => ({todayDeaths: a.todayDeaths + b.todayDeaths})).todayDeaths;
        recovered = data.reduce((a, b) => ({recovered: a.recovered + b.recovered})).recovered; // returns object
        active = data.reduce((a, b) => ({active: a.active + b.active})).active;
        critical = data.reduce((a, b) => ({critical: a.critical + b.critical})).critical;

        values.push(cases, todayCases, deaths, todayDeaths, recovered, active, critical);
        values = values;

        labels.push('cases', 'todayCases', 'deaths', 'todayDeaths', 'recovered', 'active', 'critical');
        labels = labels;
      }
    }

    afterUpdate(createChart)
  </script>

  <canvas id="breakdown"
    width="2"
    height="1"></canvas>


    <!-- <RecoveredChart data={data}> </RecoveredChart> -->