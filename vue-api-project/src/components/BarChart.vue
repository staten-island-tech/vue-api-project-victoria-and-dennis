<template>
    <PolarArea
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
    />
  </template>
  
  <script >
  import { PolarArea } from 'vue-chartjs'
  import {  Chart as ChartJS,
  RadialLinearScale,
  ArcElement,
  Tooltip,
  Legend } from 'chart.js'
  
  ChartJS.register(RadialLinearScale, ArcElement, Tooltip, Legend)
  
  export default {
    name: 'PolarChart',
    components: { PolarArea },
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

  data.forEach(o => {
    const borough = object.name
  })
  </script>
  