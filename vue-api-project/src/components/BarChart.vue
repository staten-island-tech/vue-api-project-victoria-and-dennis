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
          datasets: [ { data: [this.test,this.test2,this.test3,this.test4,this.test5] } ]
        },
        chartOptions: {
          responsive: true
        },
        loaded :false
      }
    },

    created() {
      this.chartData.datasets[0].data[0] = this.test
      this.chartData.datasets[0].data[1] = this.test2
      this.chartData.datasets[0].data[2] = this.test3
      this.chartData.datasets[0].data[3] = this.test4
      this.chartData.datasets[0].data[4] = this.test5
    },

    beforeUpdate(){
      this.chartData.datasets[0].data[0] = this.test
      this.chartData.datasets[0].data[1] = this.test2
      this.chartData.datasets[0].data[2] = this.test3
      this.chartData.datasets[0].data[3] = this.test4
      this.chartData.datasets[0].data[4] = this.test5
    },
    
    mounted() {
      this.chartData.datasets[0].data[0] = this.test
      this.chartData.datasets[0].data[1] = this.test2
      this.chartData.datasets[0].data[2] = this.test3
      this.chartData.datasets[0].data[3] = this.test4
      this.chartData.datasets[0].data[4] = this.test5
      ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
      this.loaded = true

     
        
        /* this.datasets[0].data.push(this.info[0]) 
        console.log(this.info)
        this.loaded = true */
    
    }
  }

  </script>
  