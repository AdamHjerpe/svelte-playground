<script lang="ts">
	import LineChart from './LineChart.svelte'
	import btcJson from '../data/btc-market-price.json'
	let filteredData = btcJson.values.reverse().slice(0, 10)
	let chartData: object = {
	datasets: [{
		label: 'BTC price history',
		labels: ['1','2','3','4','5','6','7','8','9','10'],
		data: filteredData,
		borderColor: '#3e95cd',
		fill: false,
	}]	
	}
	const chartOptions: object ={
		beginAtZero: true,
		parsing: {
			xAxisKey: 'x',
			yAxisKey: 'y'
		}
	}
	console.log(filteredData)
</script>

<main>
	<LineChart data={chartData} options={chartOptions}/>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>