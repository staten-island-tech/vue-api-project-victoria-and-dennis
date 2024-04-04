<template>
  <main>
    <h1>Chart representing Amount of public toilets in each Borough</h1>
    <BarChart
     :info = "valuee" 
     :test="Brooklyn" 
     :test2="StatenIsland" 
     :test3="Bronx"
     :test4="Queens"
     :test5="Manhattan"  />
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

const Brooklyn = ref(0)
const StatenIsland = ref(0)
const Bronx = ref(0)
const Queens = ref(0)
const Manhattan = ref(0)

onBeforeMount(async ()=>{
  let test = await getData()
   test.forEach(element => {
  if (element.borough === "Brooklyn"){
    Brooklyn.value++
     }
  else if(element.borough === "Staten Island"){
    StatenIsland.value++
  }
  else if(element.borough === "Bronx"){
    Bronx.value++
  }
  else if(element.borough === "Queens"){
    Queens.value++
  }
  else if(element.borough === "Manhattan"){
    Manhattan.value++
  }
}); 
loaded = true
})

console.log(toilets)

</script>



