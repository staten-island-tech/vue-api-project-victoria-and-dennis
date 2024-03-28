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
    props: {
      feces:Object
    },
    data() {
      return {
        chartData: {
          Boroughs: [ 'Handicap', 'no' ],
          datasets: [ { data: [0, 0] } ]
        },
        chartOptions: {
          responsive: true
        }
        
      }
    },
    mounted(){
      this.feces.forEach(toilet => {
        if (toilet.handicap_accessible) {
          this.chartData.datasets[0].data[0]++
        } else {
          this.chartData.datasets[0].data[1]++

        }
      })
    }
  }

  </script>
  