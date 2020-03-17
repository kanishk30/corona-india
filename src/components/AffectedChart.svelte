<script>
    export let data;
    import {
      onMount,
      afterUpdate
    } from 'svelte';
    import FusionCharts from 'fusioncharts';
    import Charts from 'fusioncharts/fusioncharts.charts';
    import FusionTheme from 'fusioncharts/themes/fusioncharts.theme.fusion';
    import SvelteFC, {
      fcRoot
    } from 'svelte-fusioncharts';

    // Always set FusionCharts as the first parameter
    fcRoot(FusionCharts, Charts, FusionTheme);

    let currentData = [];
    let chartConfigss = {};

    onMount(async () => {
      makeAffectedChart(data);
    })

    function makeAffectedChart(data) {
          for (let i = 0; i < 5; i++) {
            let obj = {};
            obj['label'] = data[i]['country'];
            obj['value'] = data[i]['cases'];
            currentData.push(obj);
          }
          let india = data.filter(o => o.country === 'India');
            let obj = {};
            obj['label'] = india[0]['country'];
            obj['value'] = india[0]['cases'];
            currentData.push(obj);

          currentData = currentData;
          const dataSource = {
            chart: {
              caption: 'Affected population',
              subCaption: '',
              xAxisName: 'Country',
              yAxisName: 'Percentage',
              numberSuffix: '',
              theme: 'fusion'
            },
            data: [...currentData]
          };

          chartConfigss = {
            type: 'column2d',
            width: 600,
            height: 400,
            dataFormat: 'json',
            dataSource: dataSource
          };

    }
  </script>
  <SvelteFC {...chartConfigss} />