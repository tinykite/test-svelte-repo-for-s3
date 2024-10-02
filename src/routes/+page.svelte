<script>
	import BarChart from '../components/BarChart.svelte';

	let data = [
		{ label: 'A', value: 30 },
		{ label: 'B', value: 80 },
		{ label: 'C', value: 45 },
		{ label: 'D', value: 60 },
		{ label: 'E', value: 20 },
		{ label: 'F', value: 90 },
		{ label: 'G', value: 55 }
	];
</script>

<main>
	<h1>Simple Bar Chart with D3 in SvelteKit</h1>
	<BarChart {data} />
</main>
