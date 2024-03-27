<template>
  <main>
    <h1>Hola</h1>
    <PolarChart/>
  </main>
</template>

<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import PolarChart from "../components/BarChart.vue"
import{ref, onMounted} from 'vue';
let toilets = ref('');
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value= data;
}
onMounted(()=>{
  getData()
})

const props = defineProps({ chartData: Array })

const Brooklyn = {}
toilets.forEach(el => {
  if (el.value.borough === "Brooklyn"){
    [Brooklyn] + 1
    
  }
})


</script>



