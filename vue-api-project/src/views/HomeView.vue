<template>
  <main>
    <h1>Hola</h1>
    <TheWelcome />
  </main>
</template>

<script setup>
import TheWelcome from '../components/TheWelcome.vue'

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

  import {Bar} from 'vue-chartjs'
</script>



