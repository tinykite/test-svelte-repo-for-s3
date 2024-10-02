<script>
	import * as d3 from 'd3';
	import { onMount } from 'svelte';

	export let data = [];

	onMount(() => {
		const svg = d3.select('#bar-chart').attr('width', 400).attr('height', 300);

		const x = d3
			.scaleBand()
			.domain(data.map((d) => d.label))
			.range([0, 400])
			.padding(0.1);

		const y = d3
			.scaleLinear()
			.domain([0, d3.max(data, (d) => d.value)])
			.nice()
			.range([300, 0]);

		svg
			.append('g')
			.selectAll('.bar')
			.data(data)
			.enter()
			.append('rect')
			.attr('class', 'bar')
			.attr('x', (d) => x(d.label))
			.attr('y', (d) => y(d.value))
			.attr('width', x.bandwidth())
			.attr('height', (d) => 300 - y(d.value));

		svg.append('g').attr('transform', 'translate(0,300)').call(d3.axisBottom(x));

		svg.append('g').call(d3.axisLeft(y));
	});
</script>

<svg id="bar-chart"></svg>

<style>
	.bar {
		fill: steelblue;
	}
	.bar:hover {
		fill: orange;
	}
</style>
