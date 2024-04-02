<!-- <template>
  <main>
    <h1>Hola</h1>
    <PolarChart :feces="toilets"/>
  </main>
</template>

<script setup>
import PolarChart from "../components/BarChart.vue"
import{ref, onMounted} from 'vue';
const toilets = ref('getData');
 async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  console.log(data)
  toilets.value= data;
}
onMounted(async()=>{
  await getData()
}) 

 const getData = async () => {
  const res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  const data = await res.json();
  console.log(data);
  toilets.value = data
} 

 onMounted(async ()=> {
  console.log("mounted")
  const res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  const data = await res.json();
  toilets.value = data
  console.log(data);
})
</script> 
 -->

 <template>
  <main>
    <h1>Hola</h1>
    <DoughnutChart :information="Values" :info1="Values.Yes" :info2="Values.No" />
  </main>
</template>

<script setup>
import DoughnutChart from "../components/DoughnutChart.vue"
import { ref, onBeforeMount } from 'vue';

const toilets = ref(getData);
let loaded= false;
async function getData() {
  let res = await fetch("https://data.cityofnewyork.us/resource/hjae-yuav.json");
  let data = await res.json();
  
  toilets= data;
  console.log(toilets)
  return data
}

const Values = {
  Yes:0,
  No:0,
}
onBeforeMount(async ()=>{
  let testy = await getData()
   testy.forEach(element => {
  if (element.OpenYearRound === "Yes"){
    Values.Yes = Values.Yes+1
     }
  else if(element.OpenYearRound === "No"){
Values.No = Values.No+1
  }
 
}); 
loaded = true
})
</script>


