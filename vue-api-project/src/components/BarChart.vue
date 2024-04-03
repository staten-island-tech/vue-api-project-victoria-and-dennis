<template>
    <Bar
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
      v-if="loaded"
    />
  </template>
  
  <script >
  import { Bar } from 'vue-chartjs'
  
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
 

  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'BarChart',
    components: { Bar },
    props: {
      info:Object,
      test:Number,
      test2:Number,
      test3:Number,
      test4:Number,
      test5:Number
    },
    data() {
      return {
        chartData: {
          labels: [ 'Brooklyn', 'Staten Island', 'Bronx', 'Queens', 'Manhattan' ],
          datasets: [ { data: [this.Brooklyn,this.StatenIsland,this.Bronx,this.Queens,this.Manhattan] } ]
        },
        chartOptions: {
          responsive: true
        },
        loaded :false
      }
    },
    mounted: function(){
      this.loaded = true
     
        
        /* this.datasets[0].data.push(this.info[0]) 
        console.log(this.info)
        this.loaded = true */
    
    }
  }

  </script>
  