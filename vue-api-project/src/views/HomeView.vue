<template>
  <main>
    <h1>Hola</h1>
    <TheWelcome />
  </main>
</template>

<script setup>
import TheWelcome from '../components/TheWelcome.vue'

import{ref, onMounted} from 'vue';
const toilets=ref('');
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  toilets.value= data.results;
}
onMounted(()=>{
  getData()
})

console.log(
  onMounted()
)
</script>



