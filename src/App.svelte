<script>
	 import {
    onMount,
    afterUpdate
  } from 'svelte';
	import Navbar from './components/Navbar.svelte';
	import Help from './components/Help.svelte';
	import CurrentData from './components/CurrentData.svelte';
	import CasesBreakup from './components/CasesBreakup.svelte';
	import DosDonts from './components/DosDonts.svelte';
	import Banner from './components/Banner.svelte';
	import Symptoms from './components/Symptoms.svelte';
	import Footer from './components/Footer.svelte';

	let isResolved = false;
	$: data = [];

	onMount(async () => {
    fetch("https://coronavirus-19-api.herokuapp.com/countries")
      .then(response => response.json())
      .then(res => {
        isResolved = true;
         data = res;
      })
  })

</script>

<Navbar />
<main>
	<Help />
	{#if isResolved}
	<CasesBreakup {data} />
	{/if}
	<Symptoms />
	{#if isResolved}
	<section>
		<Banner {data}/>
		<CurrentData {data} />
	</section>
	{/if}
	<DosDonts />
</main>
<Footer></Footer>

<style>
	section {
		display: flex;
		margin: 2rem 0;
	}
</style>