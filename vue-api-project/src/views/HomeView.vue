<template>
  <main>
    <h1>Hola</h1>
    <PolarChart :feces="toilets"/>
  </main>
</template>

<script setup>
import PolarChart from "../components/BarChart.vue"
import{ref, onMounted} from 'vue';
const toilets = ref('');
/* async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value= data;
}
onMounted(async()=>{
  await getData()
}) */

/* const getData = async () => {
  const res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  const data = await res.json();
  console.log(data);
  toilets.value = data
} */

onMounted(async ()=> {
  console.log("mounted")
  const res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  const data = await res.json();
  console.log(data);
  toilets.value = data
})
</script>



