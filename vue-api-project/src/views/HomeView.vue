<template>
  <main>
    <h1>Chart</h1>
    <BarChart
     :info = "valuee" 
     :test="valuee.Brooklyn" 
     :test2="valuee.StatenIsland" 
     :test3="valuee.Bronx"
     :test4="valuee.Queens"
     :test5="valuee.Manhattan"  />
  </main>
</template>

<script setup>

import BarChart from "../components/BarChart.vue"
import{ref, onBeforeMount} from 'vue';
let toilets = ref('getData');
let loaded = false;
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  
  toilets= data;
  console.log(toilets)
  return data
}
const valuee = {
  Brooklyn :0,
  StatenIsland :0,
  Bronx :0,
  Queens :0,
  Manhattan :0,
}

onBeforeMount(async ()=>{
  let test = await getData()
   test.forEach(element => {
  if (element.borough === "Brooklyn"){
    valuee.Brooklyn = valuee.Brooklyn+1
     }
  else if(element.borough === "Staten Island"){
valuee.StatenIsland = valuee.StatenIsland+1
  }
  else if(element.borough === "Bronx"){
    valuee.Bronx = valuee.Bronx+1
  }
  else if(element.borough === "Queens"){
    valuee.Queens = valuee.Queens+1
  }
  else if(element.borough === "Manhattan"){
    valuee.Manhattan = valuee.Manhattan+1
  }
}); 
loaded = true
})

console.log(toilets)

</script>



