<!-- <template>
    <Doughnut
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
    />
  </template>
  
  <script >
  import { Doughnut } from 'vue-chartjs'
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

  </script> -->

  <template>
    <div>
      <h2>Toilets Open Year-Round</h2>
      <Doughnut :options="chartOptions" :data="chartData" />
    </div>
  </template>
  
  <script>
  import { Doughnut } from 'vue-chartjs';
  
  export default {
    components: {
      name: 'DoughnutChart',
    components: { Doughnut },
  },
    props: {
      toilets: Array
    },
    data() {
      return {
        openYearRoundCount: 0,
        notOpenYearRoundCount: 0,
        chartData: {},
        chartOptions: {
          responsive: true,
        },
      };
    },
    created() {
      this.countOpenYearRoundToilets();
      this.createChartData();
    },
    methods: {
      countOpenYearRoundToilets() {
        this.toilets.forEach((toilet) => {
          if (toilet.open_year_round === 'Yes') {
            this.openYearRoundCount++;
          } else {
            this.notOpenYearRoundCount++;
          }
        });
      },
      createChartData() {
        this.chartData = {
          labels: ['Open Year-Round', 'Not Open Year-Round'],
          datasets: [
            {
              data: [this.openYearRoundCount, this.notOpenYearRoundCount],
              backgroundColor: ['#36A2EB', '#FF6384'],
            },
          ],
        };
      },
    },
    mounted() {
      this.renderChart(this.chartData, this.chartOptions);
    },
  };
  </script>
  
  