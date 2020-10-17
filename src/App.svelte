<script lang="ts">
	import moment from 'moment'
	import LineChart from './LineChart.svelte'
  import btcJson from '../data/btc-market-price.json'
  
	let modifiedBtcData: Array<object> = btcJson.values.map(object => ({
    x: object.x * 1000,
    y: object.y
  }));
  
	let chartData: object = {
	datasets: [{
		label: 'BTC price history',
		data: modifiedBtcData,
		borderColor: '#3e95cd',
		fill: true,
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
					},
					parser: 'X'
				},
				
			}]
		},
	}
	console.log(modifiedBtcData)
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