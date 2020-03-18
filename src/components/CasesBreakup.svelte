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
    $: mortalityRate = (((deaths + todayDeaths) / cases) * 100).toFixed(2);

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

        values.push( todayCases, deaths, todayDeaths, recovered, active, critical);
        values = values;

        labels.push('todayCases', 'deaths', 'todayDeaths', 'recovered', 'active', 'critical');
        labels = labels;
      }
    }

    afterUpdate(createChart)
  </script>

  <section>
    <div class="left">
      <p>
        COVID-19 is a new disease and world is still learning how it spreads, the severity of illness it causes, and to what extent it may spread in the world.
      </p>
      <p>
        With total number of cases being {cases}, mortality rate stands at {mortalityRate}%.
      </p>
    </div>
    <div class="right">
      <canvas id="breakdown"
        width="2"
        height="1"></canvas>
    </div>
  </section>

<style>
  section {
    display: flex;
    justify-content: space-between;
		margin: 2rem 0;
  }
  .left {
    background: #2bbdd4;
    color: white;
    padding: 24px;
    flex-basis: 50%;
  }
  p {
    color: white;
    font-size: 24px;
    line-height: 2;
  }
  .right {
  height: 80%;
  width: 80%;
  flex-basis: 50%;
  }
  </style>