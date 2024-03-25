<template>
  <main>
    <h1>Chart</h1>
    <BarChart/>
  </main>
</template>

<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import BarChart from "../components/BarChart.vue"
import{ref, onMounted} from 'vue';
let toilets = ref('');
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value = data;
}
onMounted(()=>{
  getData()
})

const text = {
  Brooklyn :0,
  StatenIsland :0,

}
toilets.value.forEach(element => {
  if (element.borough === "Brooklyn"){
    
    [text.Brooklyn]+1
  } 
});

console.log(Brooklyn)
</script>



