<script>
	 import {
    onMount,
    afterUpdate
  } from 'svelte';
	import Navbar from './components/Navbar.svelte';
	import Help from './components/Help.svelte';
	import CurrentData from './components/CurrentData.svelte';
	import DosDonts from './components/DosDonts.svelte';
	import Banner from './components/Banner.svelte';
	import Symptoms from './components/Symptoms.svelte';

	let isResolved = false;
	let data = [];

	onMount(async () => {
    fetch("https://coronavirus-19-api.herokuapp.com/countries")
      .then(response => response.json())
      .then(res => {
        isResolved = true;
         data = res;
      })
  })

</script>

<main>
	<Navbar />
	{#if isResolved}
	<Banner {data}/>
	{/if}
	<Help />
	<Symptoms />
	<DosDonts />
	{#if isResolved}
	<CurrentData {data} />
	{/if}
</main>

<style>

</style>