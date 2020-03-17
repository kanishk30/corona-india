<script>
  export let data;
  import RecoveredChart from './RecoveredChart.svelte';
  import AffectedChart from './AffectedChart.svelte';
  import {
    onMount,
    afterUpdate
  } from 'svelte';

  let api = [];
  // onMount(async () => {
  //   fetch("https://coronavirus-19-api.herokuapp.com/countries")
  //     .then(response => response.json())
  //     .then(res => {
  //       isResolved = true;
  //        data.update(curr => [...curr, ...res]);
  //       //  console.log(res, "res");
  //       //  console.log(data, "DATA");
  //     })
  // })
</script>

<AffectedChart data={data}> </AffectedChart>
<!-- <RecoveredChart data={coronaData}> </RecoveredChart> -->
