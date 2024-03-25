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
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'BarChart',
    components: { Bar },
    data() {
      return {
        chartData: {
          Boroughs: [ 'Brooklyn', 'Staten Island', 'Bronx', 'Queens', 'Manhattan' ],
          datasets: [ { data: [0, 0, 0, 0, 1] } ]
        },
        chartOptions: {
          responsive: true
        }
        
      }
    }
  }
  </script>
  