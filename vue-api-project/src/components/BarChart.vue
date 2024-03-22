<template>
    <Bar
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
    />
  </template>
  
  <script >
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  import{ref, onMounted} from 'vue';
let toilets = ref('');
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value = data;
}
onMounted(()=>{
  getData()
})

  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'BarChart',
    components: { Bar },
    data() {
      return {
        chartData: {
          labels: [ 'Brooklyn', 'Staten Island', 'Bronx', 'Queens', 'Manhattan' ],
          datasets: [ { data: [0, 0, 0, 0, 0] } ]
        },
        chartOptions: {
          responsive: true
        }
      }
    },
  }
 
  </script>
  