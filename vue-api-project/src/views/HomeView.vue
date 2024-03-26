<template>
  <main>
    <h1>Chart</h1>
    <BarChart/>
  </main>
</template>

<script setup>

import BarChart from "../components/BarChart.vue"
import{ref, onMounted} from 'vue';
let toilets = ref('getData');
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value = data;
}
const valuee = {
  Brooklyn :0,
  StatenIsland :0,
  Bronx :0,
  Queens :0,
  Manhattan :0,
}

onMounted(()=>{
  getData()
  toilets.rawValue.forEach(element => {
  if (element.borough === "Brooklyn"){
    [valuee.Brooklyn]+1
    console.log(valuee)
  } 
});
})

console.log(toilets)

</script>



