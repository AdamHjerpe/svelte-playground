<script lang="ts">
	import moment from 'moment'
	import LineChart from './LineChart.svelte'
	import btcJson from '../data/btc-market-price.json'

	let filteredData = btcJson.values.reverse().slice(0, 10)
	let chartLabels = filteredData.map(a => a.x)

	let chartData: object = {
	datasets: [{
		label: 'BTC price history',
		// labels: chartLabels.forEach(e => { moment(e * 1000).format('D, MMM, YYYY, HH:mm') }),
		data: btcJson.values,
		borderColor: '#3e95cd',
		showLine: true,
		fill: false,
	}]	
	}
	const chartOptions: object = {
		beginAtZero: true,
		scales: {
			xAxes: [{
				type: 'time',
				time: {
					// unit: 'month',
					displayFormats: {
						quarter: 'MMM YYYY'
					}
				},
				
			}]
		},
		// parsing: {
		// 	xAxisKey: 'x',
		// 	yAxisKey: 'y'
		// }
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