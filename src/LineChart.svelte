<script>
  import { onMount, afterUpdate } from 'svelte'
  import Chart from 'chart.js'

  export let data
  export let options

  console.log(data)
  const createChart = () => {
    var ctx = document.getElementById('myChart').getContext('2d');
    var myChart = new Chart(ctx, {
      type: 'line',
      data: data,
      options: options
    });
  }
  onMount(createChart)
  // afterUpdate(() => myChart.update())
  </script>
<canvas id="myChart" width="2" height="1"></canvas>